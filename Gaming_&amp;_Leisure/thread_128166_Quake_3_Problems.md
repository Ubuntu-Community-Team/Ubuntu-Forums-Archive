---
title: "Quake 3 Problems"
date: 2006-02-10
forum: Gaming &amp; Leisure
---

### Post by jdralphs on 2006-02-10
hello.

years ago i bought the linux version of quake 3 arena (the loki games version) well i tried to install it on breezy and i'm having some problems.  i run quake3 and i get the following in the console.

jdralphs@ubuntu:/usr/local/games/quake3$ quake3
Q3 1.11 linux-i386 Nov 24 1999
----- FS_Startup -----
Current search path:
/home/jdralphs/.q3a/baseq3
quake3/baseq3

----------------------

Running in restricted demo mode.

----- FS_Startup -----
Current search path:
/home/jdralphs/.q3a/demoq3
quake3/demoq3

----------------------
----- CL_Shutdown -----
-----------------------
----- CL_Shutdown -----
-----------------------
Error: Couldn't load default.cfg


Any ideas -- i've tried running it with sudo and I get the same problem.

---

### Post by jdralphs on 2006-02-11
Install worked on fresh install of Breezy (Q3 also worked on Dapper Drake)

But now after i run it i get:

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/jdralphs/.q3a/baseq3
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
...loading libGL.so: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
gd error (glide): Can't find or access Banshee/V3 board
Received signal 11, exiting...

---

### Post by jdralphs on 2006-02-14
i seem to keep on replyinng to myself -- now when i execute quake3 i get a seg fault -- any ideas?


pak0.pk3  pak2.pk3  pak4.pk3  pak6.pk3  pak8.pk3
pak1.pk3  pak3.pk3  pak5.pk3  pak7.pk3
jdralphs@Darky:/usr/local/games/quake3/baseq3$ cd ..
jdralphs@Darky:/usr/local/games/quake3$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/jdralphs/.q3a/baseq3
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
execing q3config.cfg
execing autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 4/4/4 Color bits, 16 depth, 8 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 24
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 25
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 26
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 27
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 28
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 3
  Minor opcode of failed request: 0
  Serial number of failed request: 31
GL_RENDERER: (null)
----- CL_Shutdown -----
RE_Shutdown( 1 )
Received signal 11, exiting...
/usr/local/bin/quake3: line 5:  7938 Segmentation fault      ./quake3.x86 $*

---

### Post by brownbear on 2006-07-27
[size=2]***edit*: a solution has been found**[/size]

I have a similar error dump.  The parts about not being able to find the default.cfg are to do with the quake not being able to see pak0.cfg.  The default file actually exists inside that somewhere. I've tried various things but I haven't solved it yet... you should try to recopy the pak0.cfg from the disk.  You should also make sure that your user account has access to the game files.  Also make sure that the pak0.cfg is actually in the right place.I've [read](http://planetquake.gamespy.com/View.php?view=Articles.Detail&id=148) that adding this to your command line can make it work
```
+set fs_cdpath  D:\Quake3\
```I also tried doing [this](http://justlinux.com/forum/archive/index.php/t-49742.html):
```
chown -R *username*.users /usr/local/games
```and I tried [this](http://justlinux.com/forum/archive/index.php/t-49522.html)```
./quake3 +seta r_gldriver libGL.so
```Here are two guides for q3 installation: ([1](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)), ([2](http://www.neowin.net/forum/lofiversion/index.php/t252074.html))

Linux Distribution = Ubuntu Dapper Drake 6.06
Graphics make/model/memory/driver version = Nvidia/geforce3/64MB/NVIDIA Linux x86 Kernel Module 1.0-8762
CPU model / CPU Memory = Pentium 4 1.5GHZ / 512MB 

If you solve this please post back :)
bb
------------------------
**Solution** I've done this before but it now seems to work.... I simply recopied the pak0.pk3 file into ~/*username*/.q3a/baseq3/ and it all works.  Phew...

Once I got the game running I found that the mouse wouldn't move in game.  The buttons were bound correctly, I have left click as shoot and right click as zoom.  These were working correctly.  Even the scroll was working correctly.  However it would not let me turn at all.  

The strangest part of all is that when I press Esc to go to the menu, the mouse suddenly starts to work.  I have looked for solutions but people have only suggested to make sure you are on the point-release.  I was on 1.16 and I just upgraded to 1.33 ([icculus.org](http://www.icculus.org/quake3/))... but the problem still persists.  The final anomaly is that I don't get this problem in q3demo (which is verison 1.11).  Does anyone know what I've done wrong?

---

### Post by HAARP on 2006-07-28
Could you post the mouse part of your xorg.conf?

---

### Post by brownbear on 2006-07-28
Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver   "mouse"
   Option   "CorePointer"
   Option   "Device"   "/dev/input/mice"
   Option   "Protocol"   "ExplorerPS/2"
   Option   "ZAxisMapping"   "4 5"
   Option   "Emulate3Buttons" "true"
EndSection

The mouse is an infra-red microsoft intelli mouse.  It's the basic one with 2 buttons and a scroll which acts as the third.

Thanks for reading,
bb.

---

### Post by HAARP on 2006-07-28
I have a similar problem with VMware, buttons work but movement doesn't. But that's because I modified it. You don't seem to have modified it, so I don't knwo whats happening :/
Try deleting your config.cfg (somewhere inside your home folder, but make a backup)

---

### Post by pix.tmp on 2006-09-21
To get the demo running I did the following

In /home/pix/.q3a/demoq3

1) Made a copy of q3config.cfg named default.cfg
```
cp q3config.cfg default.cfg
```

2) and a symlink to pak0.pk3
```
ln -s /usr/local/games/q3demo/demoq3/pak0.pk3 pak0.pk3
```

Smooth it ran :)

---

