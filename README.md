# SVO / Bodycam Android project

## Current prototype update
- Added touch controls for crouch and prone; the stances are mutually exclusive and movement speed is reduced.
- Camera height and weapon-viewmodel position smoothly respond to stance changes.
- Added subtle procedural idle breathing to world soldier models; existing walk/death motion remains.
- Added the supplied `ukrainian_soldier.glb` at `app/src/main/assets/models/ukrainian_soldier.glb`.

## Animation limitation
The current custom GLB loader renders static mesh primitives and does not yet implement glTF skinning, inverse-bind matrices, or animation channels. Therefore this update does not claim full bone-driven character animation or a true first-person arm mesh extracted from the selected skin. The visible weapon arms remain the existing procedural viewmodel. Full skeletal animation requires extending `GlbModel` and the OpenGL vertex pipeline to support JOINTS_0/WEIGHTS_0 and skin matrices, then loading animation clips for each fighter.


## Внешние файлы анимаций

Файлы анимаций можно хранить отдельно от `SVO-main.zip` в корне GitHub-репозитория. Текущий workflow копирует дополнительные файлы репозитория в `app/src/main/assets/user_files/`. `AnimationLibrary.find(context)` перечисляет найденные `.fbx` и `.glb` файлы в этом каталоге (включая вложенные каталоги).

**Важно:** это этап обнаружения и упаковки файлов. Текущий игровой рендерер пока не воспроизводит FBX-анимации: для этого ещё требуется FBX/glTF animation parser, skinning (JOINTS/WEIGHTS) и применение матриц костей в шейдере. Добавление FBX в репозиторий само по себе не включает анимацию в игре.
