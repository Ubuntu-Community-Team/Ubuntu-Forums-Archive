---
title: "[SOLVED] Spurious mouse pointer after idle screen lock"
date: 2015-06-08
forum: Desktop Environments
---

### Post by Peter_Horn on 2015-06-08
Hi. I'm new here, so if this thread is in the wrong forum, please point me in the right direction.
I have a fresh install of 14.04 LTS (32 bit) on an ASUS K53S laptop (dual boot with Windows, but I don't think that's relevant).
When I initially boot up or after a "close the lid" suspend, all is good.
However, if I let the screen blank after 5 minutes inactivity and the system locks, when I wake it up I get a second "NW arrow" mouse pointer stuck in the middle of the screen.
I have seen other threads on various forums mention this and they are often dismissed as non-repeatable. For me, this is certainly repeatable, and it is annoying.

[see my reply below for the solution.]

---

### Post by RobGoss on 2015-06-15
Hello and welcome, Is this a wireless mouse you're using? As far as I remember when I first started with Ubuntu I was also having problems with my Wireless mouse I even changed the battery and it help a little but since then it has seem to gone away. Not sure if it's just a glitch or what

---

### Post by Duck_Dude on 2015-06-16
Is this a Logitech mouse?  I was having issues with my Logitech mouse and excessive delay in mouse movement until I installed Solaar.  It fixed the problem immediately.  

```
sudo apt-get install solaar
```

Also, not sure what your setup is like, but when I put /home and / (root) on separate partitions, for some reason on my system, I always get keyboard and mouse delays when at the lock screen.  The system runs 100% at all other points, but at the lock screen, delays are insane.  Just something I'm throwing out there.

---

### Post by Peter_Horn on 2015-06-18
Solved it myself. I was also experiencing flickering/disappearing mouse pointer. The recommended cure for that is to disable a second screen in settings>screen display. Doing that also fixed this issue. 
It has nothing at all to do with mouse hardware.

---

