---
title: "tremulous wont come out"
date: 2007-12-12
forum: Gaming &amp; Leisure
---

### Post by Lesouteneur on 2007-12-12
I installed tremulous with synaptic. It shows up in the games section but when i click the icon it just flashes the whole screen black but nothing comes out. What can be the problem?

Please help this Linux newbie.

-edit- I have Ubuntu Gutsy and have all the updates installed.

---

### Post by MetalMusicAddict on 2007-12-12
Is compiz running? "Desktop Effects"? If so, turn them off and try. Also, what GFX card?

---

### Post by Lesouteneur on 2007-12-12
Thanks for the fast response.
I have none of those on just metacity with no effects. I think I have an intel card though not sure. But I am sure it has 128MB of memory.

---

### Post by DarwinsTheory on 2007-12-14
Try running it from the command line.. bet it has a fit about no 3D enabled.

In which case enable the restricted drivers and you should be good to go.

Matt

---

### Post by Lesouteneur on 2007-12-14
I tried running from terminal this is what it shows me:

[HTML]----- FS_Startup -----
Current search path:
/home/framirez/.tremulous/base
/usr/share/games/tremulous/base/vms-1.1.0.pk3 (4 files)
/usr/share/games/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/usr/share/games/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/usr/share/games/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/usr/share/games/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/usr/share/games/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/usr/share/games/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/usr/share/games/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/usr/share/games/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/usr/share/games/tremulous/base/data-1.1.0.pk3 (1229 files)
/usr/share/games/tremulous/base
/usr/lib/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
couldn't exec autogen.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
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
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Using 8/8/8 Color bits, 16 depth, 8 stencil display.
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
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
[/HTML]

---

