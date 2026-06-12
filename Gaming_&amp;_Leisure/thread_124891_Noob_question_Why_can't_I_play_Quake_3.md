---
title: "Noob question: Why can't I play Quake 3?"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by nexion on 2006-02-02
I'm a newbie to ubuntu, and linux in general, so I probably am going to need someone to walk me through this.  I just installed ubuntu on my P3 box.  The graphics card is a PCI ATI All in Wonder (64mgs).  Everything seems to be working fine on my box, and I absolutely LOVE ubuntu by the way.  I installed Quake 3, and when I run it, it looks like it's starting, the screen gets resized (and stays that way after it's done, I have to ctrl, alt, - to get it back).  It produces an error message: here is what it says:

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/mikenb/.q3a/baseq3
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
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
Received signal 11, exiting...

Can someone please help me out.  Any help will be greatly appreciated.  Thanks!

---

### Post by Lord Illidan on 2006-02-02
Did you install the ati 3d drivers for your card? What happens when you run ```
glxinfo
``` in the terminal?

---

### Post by nexion on 2006-02-02
Here's what happens....

name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Segmentation fault

Can you point me in the direction of the ATI drivers, because I haven't installed any extra drivers than what came with ubuntu....

---

### Post by Lord Illidan on 2006-02-02
Certainly : [https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29%7C%28drivers%29](https://wiki.ubuntu.com/BinaryDriverHowto/ATI?highlight=%28ati%29%7C%28drivers%29)

---

### Post by Perfect Storm on 2006-02-02
[http://doc.gwos.org/index.php/3D_Graphic_Cards](http://doc.gwos.org/index.php/3D_Graphic_Cards)

See if this work.

---

### Post by nexion on 2006-02-02
I tried installing those drivers... (the fglrx ones) and now I can't even get back into the GUI...

---

### Post by nexion on 2006-02-02
Scratch my last post.  I restored the x11.conf and uninstalled the fglrx drivers, and now I'm back in.  So that didn't work, and the ati drivers from the ati site don't support my card Rage128 all in wonder.  Should I try to install one of the drivers from the ati site anyway?  And if not, where else should I get drivers from?

---

### Post by Lord Illidan on 2006-02-02
Hmm.. not sure how to put it.

ATI still do not support most of their older cards under Linux, i.e., they do not provide drivers to the community for these cards like the one you have. Your best option is to upgrade your card, preferably to an NVIDIA one.

---

### Post by nexion on 2006-02-02
Ok, I switched to the onboard chip, and now this is what I get...


/home/mikenb/.q3a/baseq3
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
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
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

---

### Post by nexion on 2006-02-02
Ok, got it to work with the intel card... but it's super slow.  (because there's no hardware acceleration).

---

### Post by mikeyman on 2006-02-03
Not to mimic someone else, but for gaming an Nvidia based card is going to prove a much easier go for you. The only drawback is that the drivers are not open sourced, so you have to be careful when upgrading the kernel as the modules will need to be upgraded or reinstalled as well. I have several boxes running Nvidia and have been pleased with the drivers and performance.

---

### Post by centy on 2006-02-09
Nvidia all the way! : )

---

