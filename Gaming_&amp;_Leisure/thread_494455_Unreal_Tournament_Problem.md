---
title: "Unreal Tournament Problem"
date: 2007-07-06
forum: Gaming &amp; Leisure
---

### Post by thebdj on 2007-07-06
I am having a problem with UT that I cannot seem to figure out.  The intro moves smoothly (for the most part) with choppy audio and game play is somewhat similar, with the added bonus of the game speeding up and slowing down.

UT is the only game giving me trouble. (NWN, UT2004, RtCW, and RtCW:ET all run fine natively and Tribes 2 and Ryzom run great in Wine.)  I have tried adjusting my game speed with no success.  My CPU is not scaling (scaling is turned off and the system is reporting it at 2.13 GHz.  Here is my system rundown:

Intel Core 2 Duo E6400
nVidia 7900 GS (with the default drivers for Feisty Fawn installed)
On-board audio (that hasn't given problems with anything else)
Ubuntu 7.04 (Feisty Fawn) is installed and up-to-date


I have tried just about everything I could find over at icculus and around the ubuntu forums, but nothing seems to correct the issue.  nvidia drivers report as 1.0-9631.

Greatly appreciate the help.  (If you need any help with issues for NWN or RtCW including ET, let me know since I ran into a few that I fixed with those.  UT2K4 was the smoothest install aside from the wine games.)

---

### Post by thebdj on 2007-07-07
Well, the problem is still outstanding, but I have officially given up.  I installed and successfully run UT in Wine with absolutely no problem or slow down.  (Well, I go get an error dialog when I exit, but heck I am done playing by then.  Any help getting this to running in native though, would be appreciated.

---

### Post by jjasonj on 2007-07-10
Hi m8, im running ut2004 on fiesty too!! Have you tried installing the restricted Nvidia driver?? ive only got the 7600 gs and ut work like a charm.Also when your in a game go into console and type in NETSPEED 100001 and your fps goes through the roof:) P.s i',m [TIME]Elements in game...:)

---

### Post by Cappy on 2007-07-10
He's using nvidia-glx.

Anyway here are things that come to mind:
*Look in console for weird errors on launch
```
ut2004
```
*Make sure you don't have any CPU monitors running such as the kind that go on the desktop to make it look cooler such as gDesklets.
*You are using 32-bit?
*Have you updated your game to 3369-2?
```
sudo apt-get install libsdl1.2debian-all
```
*UT has 2 local files in its /System folder:
libSDL-1.2.so.0  openal.so
You should try to move your current /usr/lib/libSDL-1.2.so.0.11.0 to that folder and rename it to libSDL-1.2.so.0 (backup the old one). Same thing for openal.so

---

### Post by psyopper on 2007-07-11
You are using the wrong drivers for your card, first of all. The latest supported binary (non-free) drivers that Ubuntu/Canonical support are 9755 in the nvidia-glx-new package.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get remove nvidia-glx
sudo apt-get install nvidia-glx-new

```

---

