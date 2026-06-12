---
title: "Problems with running quake 3 natively"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by can3p on 2006-02-02
Quake 3 is crashing on startup with messages
```

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/demon/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Cvar_Set2: arch linux i386
Cvar_Set2: username demon

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
Cvar_Set2: cl_paused 0
Cvar_Set2: cl_running 1
----- Client Initialization Complete -----
Cvar_Set2: com_introplayed 1
Cvar_Set2: nextmap cinematic intro.RoQ
Cvar_Set2: r_uiFullScreen 1
----- R_Init -----
Warning: cvar "r_uifullscreen" given initial values: "1" and "0"
...loading opengl32: QGL_Init: Can't load opengl32 from /etc/ld.so.conf or current dir: /usr/local/games/quake3/opengl32: cannot open shared object file: No such file or directory
failed
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Couldn't get a visual
...WARNING: could not set the given mode (6)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Couldn't get a visual
...WARNING: could not set the given mode (3)
Cvar_Set2: com_errorMessage GLimp_Init() - could not load OpenGL subsystem

----- CL_Shutdown -----
Cvar_Set2: r_uiFullScreen 1
Cvar_Set2: cl_downloadName 
Cvar_Set2: sv_cheats 1
RE_Shutdown( 1 )
Cvar_Set2: cl_running 0
-----------------------
----- CL_Shutdown -----
Cvar_Set2: cl_running 0
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

I don't know what to do, because nvidia drivers are installed(I have GF4 MX440 card) and windows version of q3 works perfectly through wine.
I've searched with google a lot but found nothing.
How to fix this problem?

---

### Post by can3p on 2006-07-06
I've just deleted all the config files from the ~/.q3a and game started to work.
The problem was with one of the r_ params

---

