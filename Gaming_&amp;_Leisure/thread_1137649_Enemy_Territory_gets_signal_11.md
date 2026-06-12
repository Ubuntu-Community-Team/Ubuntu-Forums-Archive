---
title: "Enemy Territory gets signal 11"
date: 2009-04-25
forum: Gaming &amp; Leisure
---

### Post by nachomania on 2009-04-25
After a few weeks, I decided I was in the mood for some ET, but something seems to have messed things up since I was using hardy. Compiz is working great, and videos are playing perfectly fine. Nexuiz is working too, so I'm puzzled about what's going on here. .etwolf is empty, and belongs to me. 

```
nachoman@orange-cat:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/nachoman/.etwolf/etmain
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
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 48
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 53
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 53
Received signal 11, exiting...
Segmentation fault

```

After it quits, my resolution drops from 1280x1024 to 800x600.

---

### Post by tigergibb on 2009-04-28
I can verify this problem; same exact thing happens to me. I run an Asus F3JP laptop with an ATI Radeon Mobility X1700 graphics card. I just did a fresh install of Jaunty. Can't find my video drivers anywhere.

---

### Post by tigergibb on 2009-04-28
As an update, I downloaded to Ubuntu 8.10, Intrepid Ibex, and it let me use the FGLRX proprietary video drivers which were not available in Jaunty. It works fine for me now. I'd love to update to Jaunty again if anyone can find a fix for this.

---

### Post by nachomania on 2009-04-28
I have an ATI Radeon 7200. This game used to work before jaunty, and only this game specifically has stopped working.

---

### Post by nachomania on 2009-04-30
How did you downgrade?

---

### Post by tigergibb on 2009-04-30
I reformatted and installed Intrepid. I had the ISO already downloaded from a while ago. You can still download it.. just choose Ubuntu 8.04 on the download page(I had 8.10 but it's no big deal). If you really want 8.10:

[http://www.google.com/search?hl=en&q=download+ubuntu+8.10&btnG=Google+Search&cts=1241112020838&aq=f&oq=](http://www.google.com/search?hl=en&q=download+ubuntu+8.10&btnG=Google+Search&cts=1241112020838&aq=f&oq=)

---

