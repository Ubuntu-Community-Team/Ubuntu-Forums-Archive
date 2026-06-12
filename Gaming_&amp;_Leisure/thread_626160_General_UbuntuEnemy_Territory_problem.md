---
title: "General Ubuntu/Enemy Territory problem"
date: 2007-11-28
forum: Gaming &amp; Leisure
---

### Post by Tough Juice on 2007-11-28
Sup fellas,

I'm having trouble installing ET on Linux (Ubuntu) and was told to go here with problems. I installed Ubuntu smoothly and downloded ET 2.60 for Linux and followed these instructions:

Download ET for Linux
Open Terminal - type "sudo apt-get install libgtk1.2" (this installed fine)
Now run ET in terminal (if you have any permission errors type:

chmod +x et-linux-2.60.x86.run

Ok, I ran it in terminal and this is what occured:

> Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install........................................... .................................................. .................................................. .................................................. .................................................. .................................................. .........................


Nothing then happens, it just stays paused at this and I left it there for a fair while. I was in Super User mode at the time as well.

Appreciate some help.

---

### Post by scrooge_74 on 2007-11-28
if you open a terminal and type et, what happnes?

I had my share of problems trying to run ET on Ubuntu, could never connect or make it download maps correctly.  That was a couple of months ago, I changed to Debian and ET runs perfectly now

---

### Post by Tough Juice on 2007-11-28
> **scrooge_74 said:**
> if you open a terminal and type et, what happnes?

I had my share of problems trying to run ET on Ubuntu, could never connect or make it download maps correctly.  That was a couple of months ago, I changed to Debian and ET runs perfectly now

et: command not found.

---

### Post by scrooge_74 on 2007-11-28
try installing as a normal user

---

### Post by Tough Juice on 2007-11-28
Still the same thing, also it's worth noting that the terminal and the whole Ubuntu actually freezes as well while it says uncompressing ET 2.60 and im forced to restart the comp.

BTW I thought it could be corrupt file, so i downloded ET 2.56 and the same thing happens.

---

### Post by houstonbofh on 2007-11-28
Try the howto here.
[http://katanoon.nl/ubu-e/install.php](http://katanoon.nl/ubu-e/install.php)
If you still have trouble, post back...

---

### Post by Tough Juice on 2007-11-28
Did all steps (except downloading ET 2.60 again as I already have the exact same file) and still have the same issue - Ubuntu and the terminal freezes while it says uncompressing ET 2.60 full install.

---

### Post by Tough Juice on 2007-11-29
Doesn't look like getting resolved, guess I'll have to get Debian and try.

---

### Post by Tough Juice on 2007-11-29
OK, It's installed but when I open ET in terminal I get this:

> ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
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
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

---

### Post by scrooge_74 on 2007-11-29
It seems you are having issues with your 3D card, do you have 3D acceleration enable?

---

### Post by Tough Juice on 2007-11-29
> **scrooge_74 said:**
> It seems you are having issues with your 3D card, do you have 3D acceleration enable?

How do I enable this? btw, I have an ATI x1600 PRO graphics card.

---

### Post by scrooge_74 on 2007-11-29
Did you check the help pages? [https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI](https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI)

---

