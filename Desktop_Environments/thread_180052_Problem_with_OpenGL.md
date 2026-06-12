---
title: "Problem with OpenGL"
date: 2006-05-21
forum: Desktop Environments
---

### Post by govedarov on 2006-05-21
I installed recently one game , called Return to the castle wolfensten. Everything went fine, till the point when I tried to start it. Then I get the following warning in the shell : 

> ivan@120-196:~$ wolf
Wolf 1.3 linux-i386 Mar 16 2002
----- FS_Startup -----
Current search path:
/home/ivan/.wolf/main
/usr/local/games/wolfenstein/main/mp_pakmaps1.pk3 (34 files)
/usr/local/games/wolfenstein/main/mp_pakmaps0.pk3 (21 files)
/usr/local/games/wolfenstein/main/mp_pak3.pk3 (76 files)
/usr/local/games/wolfenstein/main/mp_pak2.pk3 (3 files)
/usr/local/games/wolfenstein/main/mp_pak1.pk3 (308 files)
/usr/local/games/wolfenstein/main/mp_pak0.pk3 (783 files)
/usr/local/games/wolfenstein/main/mp_bin.pk3 (5 files)
/usr/local/games/wolfenstein/main/pak0.pk3 (4775 files)
/usr/local/games/wolfenstein/main

----------------------
6005 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec wolfconfig_mp.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Joystick is not active.
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Loaded 714 translation strings from scripts/translation.cfg
Loaded 71 translation strings from translations/icelab.cfg
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

ivan@120-196:~$


My desktop resolution also changes , and everything starts to look very ugly ::) and I cant do much, only option I see is to logout, then everything goes back to normal.
So does anyone have an idea how to fix this OpenGL issue ?

---

### Post by tseliot on 2006-05-21
I have never played that game. Nonetheless I think that you should reinstall the drivers for your graphic card so as to fix your OpenGL libraries

---

