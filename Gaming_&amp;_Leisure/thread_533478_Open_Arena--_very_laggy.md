---
title: "Open Arena-- very laggy"
date: 2007-08-24
forum: Gaming &amp; Leisure
---

### Post by akiratheoni on 2007-08-24
My system is a Gateway GM5442... Intel Core 2 Duo E4400, Intel GMA 950, 2048MB RAM. I have a Westinghouse LCM-22w 22 inch monitor.

I'm using two versions of OpenArena (both of which are 0.7). One of them is through wine, the other was installed using a *.deb file.

The one through wine works but it's extremely laggy at ANY resolution except for something like 320x200 or something too small to play the game in.

The one that I installed with the *.deb file, I get this message when I run it through the terminal:

```
[: 23: ==: unexpected operator
[: 23: ==: unexpected operator
[: 30: ==: unexpected operator
ioQ3 1.33+oa linux-i386 Jul 10 2007
----- FS_Startup -----
Current search path:
/home/abong/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (191 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (11 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1496 files)
/usr/share/games/openarena/baseoa/pak3-music.pk3 (9 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (620 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (171 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (73 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (926 files)
/usr/share/games/openarena/baseoa
/usr/lib/games/openarena/baseoa

----------------------
3497 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
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
SDL_SetVideoMode failed: Couldn't find matching GLX visual
SDL_SetVideoMode failed: Couldn't find matching GLX visual
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
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

I did what it said and added the "+set r_allowSoftwareGL 1" but that did nothing.

Help, with either version? Please? :(

---

### Post by KingHanco on 2007-08-24
Heh there is your problem right there. Mesa driver instead of graphics card drivers. Install your graphics card drivers and it should take care of that.

You can change the game screen size. I never try wine out so I can't help you there.

---

### Post by akiratheoni on 2007-08-24
With my intel gma 950, my driver would be the xserver-xorg-video-intel, which I've already installed. I just used the sudo dpkg-reconfigure xserver-xorg and changed the driver to either i810 or intel. But I still get that 'mesa' error no matter which driver I configured it to. Am I doing it wrong?

---

### Post by KingHanco on 2007-08-24
Did you went to Restricted Drivers Manager and see what it say on the screen?

If it say i810 or intel or anything else then enabled it and it will install your graphics drivers. Reboot after that. Mesa should be replace after reboot.

By the way. Don't do anything after this.

---

### Post by disturbedite on 2007-08-24
uh, i don't have any problems like this, but i have the intel driver installed but it does not show up in the restricted-manager...

btw, i can run open arena at full speed with a really crappy video card and everything turned up to high.  (including the resolution).

---

### Post by akiratheoni on 2007-08-24
> **KingHanco said:**
> Did you went to Restricted Drivers Manager and see what it say on the screen?

If it say i810 or intel or anything else then enabled it and it will install your graphics drivers. Reboot after that. Mesa should be replace after reboot.

By the way. Don't do anything after this.

Said I don't need any restricted drivers.

I found a site: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html) with instructions with Mesa drivers and such. I'm following the instructions for it.

---

### Post by Quasaur on 2007-12-17
i installed the deb package for openarean 0.6.0, then purged it for the 0.7.0 with patch. 
Since that time openarena has run perfectly...til my most recent session when i got the same error you did.

in any case, when i check restricted drivers the fglrx was disabled (?), though I dont know why. I reenabled it and will reload.


...turns out that the restricted xorg driver was disabled (for some unknown reason). Re-enabling the driver solved the problem.

My system specs:

```
Platform (Laptop): Dell Inspiron E1505 (Model MM061)
Platform BIOS: A13
Processor: Intel Core 2 Duo T5600
Ethernet Controller Broadcom BCM4401-B0 with wireless
Video Adapter: ATI Mobility Radeon X1300
Video BIOS: BK-ATI VER009.012.001.009.020855
Video Memory: 64MB
Video Driver(xorg-driver-fglrx): Version 8.37.6 (X.org 7.1.0)
Sound Card: SigmaTel STAC9200
Sound Driver: Alsa 1.0.14-1ubuntu2
Distro: Kubuntu Gutsy Gibbon (7.10)
Linux Kernel: 2.6.22-14-generic
xserver-xorg: 7.2-5ubuntu13
xserver-xorg-core: 1.3.0.0.dsfg-12ubuntu8
Kubuntu-Desktop:  1.59
KDE: 3.5.8
OpenArena: 0.7.1
```

---

