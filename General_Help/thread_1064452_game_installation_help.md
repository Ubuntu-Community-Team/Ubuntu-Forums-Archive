---
title: "game installation help"
date: 2009-02-08
forum: General Help
---

### Post by drew.saltarelli on 2009-02-08
Hey all,

so I decided to look for some good games to run with Ubuntu, and I downloaded Tremulous via the Synaptic Packet Manager, and it downloaded and installed fine, the link for the game is in applications>games>tremulous, but when I click it, nothing opens, is there something I'm missing?

---

### Post by taurus on 2009-02-08
Maybe try running it from a terminal to see what's wrong with it.

Applications -> Accessories -> Terminal
```
tremulous
```

---

### Post by drew.saltarelli on 2009-02-09
Ran via terminal, got the following error

tremulous 1.1.0 linux-x86 Sep  6 2008
----- FS_Startup -----
Current search path:
/home/drew/.tremulous/base
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
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

---

### Post by personjerry on 2009-02-09
may have something to do with your display config, go to System -> Preferences -> Screen Resolution, and state the choices for the screen resolution please, or post the contents of /etc/X11/xorg.conf

---

### Post by glotz on 2009-02-09
What kind of a video card do you have? You might need drivers for 3D.```
sudo lshw -class display
```

Does glxgears work? :)
```
glxgears
```

---

### Post by drew.saltarelli on 2009-02-09
@ personjerry, the resolution is 1280:1024


@ glotz this is what i got for the video card
*-display UNCLAIMED     
       description: VGA compatible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list
       configuration: latency=32 mingnt=2

and when I run glxgears I get the following error
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by Ng Oon-Ee on 2009-02-09
GLX is not enabled for your display driver. It looks like you have an onboard driver, so unfortunately I can't help you (i'm only familiar with xorg.conf for nvidia cards), however there should be xorg flags which enable GLX for you.

Try googling your video driver + GLX + linux, you may find some help.

---

### Post by drew.saltarelli on 2009-02-09
forget it, i just uninstalled it, 2flashgames is all I need, this computer is mainly for programming anyway, thanks for your suggestions though guys

---

