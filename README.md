Shockolate - System Shock, but cross platform!
============================
Based on the source code for PowerPC released by Night Dive Studios, Incorporated.

[![Build Status TravisCI](https://travis-ci.org/Interrupt/systemshock.svg?branch=master)](https://travis-ci.org/Interrupt/systemshock) [![Build Status AppVeyor](https://ci.appveyor.com/api/projects/status/5fmcswq8n7ni0o9j/branch/master?svg=true)](https://ci.appveyor.com/project/Interrupt/systemshock)

GENERAL NOTES
=============

This version of Shockolate is going to have some extra stuff. It is described below.

Changes:
========

- Preferences and Keybinds are now stored in `Meeper/SystemShock` instead of `Interrupt/SystemShock` for organization purposes.
- Field of View is 110 degrees until FOV Slider is implemented.

Added Features so far:
======================

- **_Toggleable Persistent Mouselook_**  
Default: Off  
Description: Located in options menu. When on, your mouse will stay locked to the center of the screen when picking up an item or opening a container. I added this because I prefer to play that way, locking and unlocking the mouse manually, and so do some other people. It's mainly for muscle memory actually.

- **_Keyboard Keypad Support_**  
Description: Changes in-game keypad binds to use your keyboard's keypad instead of the row of number keys at the top. That way, the number keys are still availible for toggling hardware implants.

- **_Extra Digital Audio Channels_**  
Default: 32  
Description: Normally, you may choose from 2, 4, or 8 digital audio channels in the audio options. Now, you may additionally choose 16 or 32 channels. I added this because there are semi-rare cases when all channels are easily filled up, such as the room with all the Z-44 Plastique (TM) on the Storage level. Now I know 32 is totally overkill, but who knows? Maybe someday there will be a reason to have 32 channels.

Planned and/or WIP Features:
============================

- **_Field of View Slider_**
- **_Widescreen Resolutions and Custom Width/Height Resolutions_** (Don't expect that anytime soon, I'm quite new to this. But I'll do my best.)

Important Requirements
======================

  - CD-ROM or SS:EE `DATA` folder in a `res` folder next to the executable
    - Floppy disk assets cannot be loaded.
  - If you have the Steam release, System Shock: Classic, you can go into `steamapps/common/SS1/SSHOCK` and find the `DATA` folder there.
    - The `SOUND` folder may also be found there. It is optional, but required if you want music. It goes inside `res` alongside `DATA`.


Running
=======

## From a prebuilt package

Currently, I have uploaded no prebuilt packages. However, I'll leave a link to the original Shockolate builds [here](https://github.com/Interrupt/systemshock/releases/).

## From source code

Prerequisites: 
- [CMake](https://cmake.org/download/) installed

Step 1. Build the dependencies:
* Windows: `build_win32.sh` or `build_win64.sh` (Git Bash and MinGW recommended)
* Linux/Mac: `build_deps.sh` or the CI build scripts in `osx-linux`
* Other: `build_deps.sh` 

Step 2. Build and run the game itself
```
cmake .
make systemshock
./systemshock
```

The following CMake options are supported in the build process:
* `ENABLE_SDL2` - use system or bundled SDL2 (ON/BUNDLED, default BUNDLED)
* `ENABLE_SOUND` - enable sound support (requires SDL2_mixer, ON/BUNDLED/OFF, default is BUNDLED)
* `ENABLE_FLUIDSYNTH` - enable FluidSynth MIDI support (ON/BUNDLED/OFF, default is BUNDLED)
* `ENABLE_OPENGL` - enable OpenGL support (ON/OFF, default ON)

If you find yourself needing to modify the build script for Shockolate itself, `CMakeLists.txt` is the place to look into.


Command line parameters
============

`-nosplash` Disables the splash screens, causes the game to start straight to the main menu

Modding Support
============
Shockolate supports loading mods and full on fan missions. Just point the executable at a mod file or folder and the game will load it in. So far mod loading supports additional `.res` and `.dat` files for resources and missions respectively.

Run a fan mission from a folder:
```
./systemshock /Path/To/My/Mission
```

Run a fan mission from specific files:
```
./systemshock my-archive.dat my-strings.res
```

Control modifications
=======

## Movement

Shockolate replaces the original game's movement with WASD controls, and uses `F` as the mouselook toggle hotkey. This differs from the Enhanced Edition's usage of `E` as the mouselook hotkey, but allows us to keep `Q` and `E` available for leaning.

## Additional hotkeys

* `Ctrl+G` cycles between graphics rendering modes
* `Ctrl+F` to enable full screen mode
* `Ctrl+D` to disable full screen mode 

