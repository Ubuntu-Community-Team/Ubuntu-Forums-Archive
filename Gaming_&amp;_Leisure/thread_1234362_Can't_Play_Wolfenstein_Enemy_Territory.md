---
title: "Can't Play Wolfenstein Enemy Territory"
date: 2009-08-07
forum: Gaming &amp; Leisure
---

### Post by zkriesse on 2009-08-07
I downloaded Wolfenstein EnemyTerritory and when I run it in the terminal this is what I get. zach@zach-laptop:~$ ./et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/zach/.etwolf/etmain
/home/zach/enemy-territory/etmain/pak2.pk3 (22 files)
/home/zach/enemy-territory/etmain/pak1.pk3 (10 files)
/home/zach/enemy-territory/etmain/pak0.pk3 (3725 files)
/home/zach/enemy-territory/etmain/mp_bin.pk3 (6 files)
/home/zach/enemy-territory/etmain

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

After I get that my screen res goes from 1680x1050 to the lowest setting...any help or ideas would be nice. Thanks

---

### Post by BoltBlue on 2009-08-07
Are you using an Intel graphics chip?

---

### Post by magmon on 2009-08-08
Have you tried using the icon instead of the terminal? Does it give the same code?

---

### Post by zkriesse on 2009-08-08
Think it's an ATI driver...and it just won't work....don't know why....

---

### Post by pwnfactory on 2009-08-28
I have the same problem... any solutions??

---

### Post by zkriesse on 2009-08-29
None whatsoever man.

---

### Post by JerTech on 2009-08-30
How can this be marked as solved when it is clearly not solved?

I also have the same problem.  I am using Linux Mint 9.04 32-bit with an ATI Radeon X850 XT.

I have searched other forums for solutions to this problem.  It seems that those experiencing this issue are using some version of Ubuntu 9.04 and an older Radeon card that is no longer supported by the ATI proprietary drivers.

Basically, we're stuck using the open source drivers and Wolfenstein doesn't seem to like them.

---

### Post by Perfect Storm on 2009-08-30
> **JerTech said:**
> How can this be marked as solved when it is clearly not solved?



Fixed

---

### Post by zkriesse on 2009-09-01
I'm no longer using this game...that is why it's marked solved...because I'm NOT installing it. Please do not be angry, it's just I gave up on people answering my thread....so I'm not going to use the game or even try.

---

### Post by NRDNick on 2009-10-13
FWIW Invalid pk3 means there is a conflict with another version of the map you are trying to load. This can happen when you play on different servers with different versions of maps. 

To fix the issue you can just search for the pk3 file of the map you were trying to load and delete it. it should be in you /home/<username>/.etwolf/etmain folder. A quick google search turns up alot on the issue. I hate lose a prospective W:ET player, for such a silly issue. I hope you try the game again :) Feel free to PM me if you have any more trouble, and come frag at Whosgaming.com.

---

