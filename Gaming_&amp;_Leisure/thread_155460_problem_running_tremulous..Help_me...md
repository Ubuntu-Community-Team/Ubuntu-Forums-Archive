---
title: "problem running tremulous..Help me.."
date: 2006-04-05
forum: Gaming &amp; Leisure
---

### Post by sands on 2006-04-05
sandesh@sandesh:~/tremulous$ ./tremulous.x86
tremulous 1.1.0 linux-x86 Feb 28 2006
----- FS_Startup -----
Current search path:
/home/sandesh/.tremulous/base
/home/sandesh/tremulous/base/vms-1.1.0.pk3 (4 files)
/home/sandesh/tremulous/base/map-uncreation-1.1.0.pk3 (110 files)
/home/sandesh/tremulous/base/map-tremor-1.1.0.pk3 (45 files)
/home/sandesh/tremulous/base/map-transit-1.1.0.pk3 (135 files)
/home/sandesh/tremulous/base/map-niveus-1.1.0.pk3 (134 files)
/home/sandesh/tremulous/base/map-nexus6-1.1.0.pk3 (151 files)
/home/sandesh/tremulous/base/map-karith-1.1.0.pk3 (118 files)
/home/sandesh/tremulous/base/map-atcs-1.1.0.pk3 (87 files)
/home/sandesh/tremulous/base/map-arachnid2-1.1.0.pk3 (67 files)
/home/sandesh/tremulous/base/data-1.1.0.pk3 (1229 files)
/home/sandesh/tremulous/base

----------------------
2080 files in pk3 files
execing default.cfg
execing autogen.cfg
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
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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





Also tried        "./tremulous +set r_allowSoftwareGL 1"

Its tooo slow..

---

### Post by localzuk on 2006-04-05
What graphics card do you have? It appears that you do not have any hardware 3D acceleration.

---

### Post by sands on 2006-04-05
How to know that??

---

### Post by Toxicity999 on 2006-04-05
It kind of looks like it's saying to you:

Initializing...
Can't find any hardware video support, rolling back to software alone.
CANT FIND MESA THE END OF THE WORLD IS UPON US!

Well... What I say to you is check into what graphics card you have (if its a newer-ish ATi then search for fglrx in the repos, install it then do something like

sudo gedit /etc/X11/xorg.conf

check ati to fglrx etc etc blah blah Of course do *NOT* follow this I was just running you through the ease of doing it. Search around for FGLRX installation or nVidia driver installation. Naturally depending on which you have.

as for actually finding out you hardware type... just goto your manufacturers site and search for your model and get a spec list of some sort. Sure to find what you need there (otherwise... they suck. hah.)

---

### Post by christooss on 2006-04-10
I have same problem. I have ati radeon 7000. I have driver section set to ati. Yesterday I run dpkg-reconfigure xserver-xorg. And now quake 3 doesn't work any more.

It was working with default "ati" drivers yesterday but not any more today.

Do I have to load aditional Modules in xorg.conf??
Cause maybe the yesterdays reconfigure erased something?

Please help :)

---

