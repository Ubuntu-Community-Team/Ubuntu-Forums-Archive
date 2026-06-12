---
title: "wolfenstein enemy territory problem need help"
date: 2008-06-28
forum: Gaming &amp; Leisure
---

### Post by videoman1994 on 2008-06-28
whenever I type in et in the console I get this

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/darren/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

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
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 134
  Minor opcode of failed request: 10
  Serial number of failed request: 55
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

could you guys help me find where my problem may be occurring.

---

### Post by lillypop on 2008-06-29
You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.

You need to install drivers for you graphics card that support opengl
Et won't run without open gl software.

---

