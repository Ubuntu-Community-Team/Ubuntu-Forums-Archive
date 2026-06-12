---
title: "Problems with Open Arena"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Stuki on 2007-08-07
I installed OA from the Add/Remove and when I try to start OA it logs me off from ubuntu. What have I done wrong?

---

### Post by Sindwiller on 2007-08-07
> **Stuki said:**
> I installed OA from the Add/Remove and when I try to start OA it logs me off from ubuntu. What have I done wrong?

You don't have the needed 3d drivers installed?

**_ATI-Cards_**

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

**_NVIDIA-Cards_**

```
sudo apt-get install nvidia-glx && sudo nvidia-xconfig
```
(or something like that - I'm not on a Linux machine right now, so I can't check...)

**_Intel-Chipset_**

No idea, shouldn't they be installed and fully configured by default?

---

### Post by Stuki on 2007-08-07
> **Sindwiller said:**
> You don't have the needed 3d drivers installed?

**_ATI-Cards_**

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

**_NVIDIA-Cards_**

```
sudo apt-get install nvidia-glx && sudo nvidia-xconfig
```
(or something like that - I'm not on a Linux machine right now, so I can't check...)

**_Intel-Chipset_**

No idea, shouldn't they be installed and fully configured by default?
I'm have the Intel-chipset...

---

### Post by weezalxc on 2007-12-24
i have the intel chipset as well...does anyone know how to fix this??

---

### Post by weezalxc on 2007-12-24
Here is what I get when I try to run "openarena" from a terminal...


weezalxc@weezal:~$ openarena 
ioQ3 1.33+oa linux-i386 Jul  5 2007
----- FS_Startup -----
Current search path:
/home/weezalxc/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (96 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (7 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (932 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (187 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (25 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (748 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
1995 files in pk3 files
execing default.cfg
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----

------- Input Initialization -------
Joystick is not active.
------------------------------------
...loading libGL.so.1:
Calling SDL_Init(SDL_INIT_VIDEO)...
SDL_Init(SDL_INIT_VIDEO) passed.
Initializing OpenGL display
...setting mode 3: 640 480
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

