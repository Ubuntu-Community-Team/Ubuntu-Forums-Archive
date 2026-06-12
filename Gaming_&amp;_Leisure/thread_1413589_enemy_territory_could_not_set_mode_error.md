---
title: "enemy territory could not set mode error"
date: 2010-02-22
forum: Gaming &amp; Leisure
---

### Post by akos.maroy on 2010-02-22
I'm trying to start Enemy Territory, but I get the following error:

```
 $ et
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/maroy/.etwolf/etmain
/opt/games/enemy-territory/etmain/pak2.pk3 (22 files)
/opt/games/enemy-territory/etmain/pak1.pk3 (10 files)
/opt/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/opt/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/opt/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


```

I saw similar threads to this effect, like this one: [http://ubuntuforums.org/archive/index.php/t-663566.html](http://ubuntuforums.org/archive/index.php/t-663566.html) - but no real conclusions there either.

on the same system, glgears, open arena and other 3D stuff run fine. this is on a 9.10 64 bit, with binary ATI drivers (10.2). glxinfo also notes a working direct acceleration:

```
$ glxinfo | grep direct
direct rendering: Yes

```

could this be an issue with color depth, for example?

---

