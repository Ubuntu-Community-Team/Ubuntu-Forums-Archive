---
title: "Games Not Booting?"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by Tumpster on 2007-08-07
So, I have UT2004 loaded along with Quake 3 on my ubuntu dapper machine. Up until last night they ran beautifully and gorgeously and now when I try to go and run them the start ups show up but when they are suppose to click over to the actual game menus it goes back to the desktop. The mini startup for ut2004 shows up and then disappears and then nothing.......Q3 flips over to the black screen for a moment then disappears to the desktop again. Both are like they are crashing. What could be causing this? I haven't changed anything really, everything as it is. It's always on startup, I've attempted rebooting and shuting down and restarting to no avail. Any help or ideas would be greatly appreciated!! :) Thanks!!!

---

### Post by DoktorSeven on 2007-08-07
If you run them from a terminal, what do you get as output?

---

### Post by Tumpster on 2007-08-08
Here is the UT2004 Bit:

craig@craig-desktop:~/ut2004$ $/home/craig/ut2004/ut2004
bash: $/home/craig/ut2004/ut2004: No such file or directory
craig@craig-desktop:~/ut2004$ /home/craig/ut2004/ut2004
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
WARNING: ALC_EXT_capture is subject to change!
Couldn't set video mode: Couldn't find matching GLX visual


History:

Exiting due to error
craig@craig-desktop:~/ut2004$

---

### Post by Tumpster on 2007-08-08
Here is the quake 3 one:

craig@craig-desktop:~/quake3$ /home/craig/quake3/quake3-smp
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/craig/.q3a/baseq3
/home/craig/quake3/baseq3/pak8.pk3 (9 files)
/home/craig/quake3/baseq3/pak7.pk3 (4 files)
/home/craig/quake3/baseq3/pak6.pk3 (64 files)
/home/craig/quake3/baseq3/pak5.pk3 (7 files)
/home/craig/quake3/baseq3/pak4.pk3 (272 files)
/home/craig/quake3/baseq3/pak3.pk3 (4 files)
/home/craig/quake3/baseq3/pak2.pk3 (148 files)
/home/craig/quake3/baseq3/pak1.pk3 (26 files)
/home/craig/quake3/baseq3/pak0.pk3 (3539 files)
/home/craig/quake3/baseq3
./quake3-smp.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
execing q3config.cfg
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
...setting mode 7: 1152 864
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1152x864
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (7)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...
craig@craig-desktop:~/quake3$

---

### Post by DoktorSeven on 2007-08-08
You don't have 3d drivers installed.  For NVidia and ATi in Ubuntu Feisty(and maybe others, not sure), do System->Administration->Restricted Drivers Manager.  Search the forums and around for other cards and/or versions.

You want the following line typed into the terminal:

**glxinfo | grep direct**

to return "direct rendering: Yes".

---

### Post by Tumpster on 2007-08-08
I get "No" for some reason, even though I just installed the new ati drivers?! Any ideas?

---

### Post by AceofAzrogoth on 2007-08-13
I have this for Wolfenstein ET, and so I installed the ati restricted driver(s), but no change.
```

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/asa/.etwolf/etmain
/usr/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/games/enemy-territory/etmain

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
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...
```

Thanks

---

### Post by hikaricore on 2007-08-13
Ace:  What method did you install the ATI drivers with?

---

### Post by Tumpster on 2007-08-13
I will usually install with the package I download off of ATI's website, but then it reverts back to mesa drivers.

---

### Post by AceofAzrogoth on 2007-08-13
I am trying the restricted driver download and install again. I can't remember exactly what I did, but this time if it does not work, it will be fresher in my memory.

---

### Post by AceofAzrogoth on 2007-08-21
okay, heres the code from the attempted install. it failed after all.](*,)

> asa@asa-desktop:~$ cd /home/asa/Desktop
asa@asa-desktop:~/Desktop$ sh ./ati-driver-installer-8.28.8.run
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.2.0

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        Unknown X Window
    x710_64a    Unknown X Window
Removing temporary directory: fglrx-install


---

### Post by remick182 on 2007-09-16
I am having a similar issue with my Return to Castle Wolfenstein install.  I downloaded the binaries and copied over the required .pak files from my Windows install, but always get a signal 11 halfway through the 'Loading' screen.  Whether I start from the beginning of the game, or try to load a saved game, it does the same thing.  I tried to reduce the graphics to the lowest settings in case that was an issue.  I also tried using the 'unset LD_PRELOAD' extension, but I believe that needs to be done from the in-game terminal.  Still, no joy.  I have read that the coding is very similar to that of Quake III, but I have yet to come across a fix.  I can install and run RTCW through WINE, but it's choppy as hell when looking left and right, and runs a little sluggish, too.  ET runs great at high res on the same computer using native Linux bins.
Also, my glxinfo | grep direct = yes

> 
dustin@toshiba-laptop:~$ sudo sh wolfsp unset LD_PRELOAD
Wolf 1.41 linux-i386 Dec  4 2002
----- FS_Startup -----
Current search path:
/home/dustin/.wolf/main
/home/dustin/wolfenstein/main/sp_pak3.pk3 (14 files)
/home/dustin/wolfenstein/main/sp_pak2.pk3 (232 files)
/home/dustin/wolfenstein/main/sp_pak1.pk3 (1342 files)
/home/dustin/wolfenstein/main/pak0.pk3 (4775 files)
/home/dustin/wolfenstein/main

----------------------
6363 files in pk3 files
execing default.cfg
couldn't exec language.cfg
execing wolfconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
Bypassing CD checks
----- Client Initialization -----
Cmd_AddCommand: map_restart already defined
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension:  Ignored on non-fullscreen/Voodoo
Using 4/4/4 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: RADEON XPRESS Series
*** IGNORING OPENGL EXTENSIONS ***
XF86 Gamma extension initialized

*******

LOADING...  - weapons
LOADING...  - items
LOADING...  - inline models
LOADING...  - server models
LOADING...  - particles
r_rmse of 0.000000 has saved 1104kb
LOADING...  - game media done
LOADING... flamechunks
LOADING... clients
LOADING... WolfPlayer
UI menu load time = 4 milli seconds
Received signal 11, exiting...
Shutdown tty console


**I found a fix, but it broke my sound.  Segment 11 is a sound issue which I fixed by installing PulseAudio under the Ubuntu:Feisty guide under 'Sound.'  However, now I am trying to get sound working again and it's been painful.  Beware in advance unless you are good with ASLA.  I'll repost once I get an answer.**

---

