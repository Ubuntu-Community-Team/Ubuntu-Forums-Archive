---
title: "q3demo, no hardware acceleration!"
date: 2006-04-13
forum: Desktop Environments
---

### Post by El Rey de Todo on 2006-04-13
I've been trying all night to get the quake3 demo running in ubuntu and I'm all out of ideas on how to fix it.

The first problem I had was a complaint that libGL.so didn't exist.  So I linked it to libGL.so.1.2 from my Xorg install.  Unfortunatly this gave my Mesa indirect rendering at about 2 frames a second.  That was aterrible.

I used locate and that sure is the only libGL.so on my computer, so I have no idea what else to do to get accellerated rendering to work for it.  I'm using this primarily for a benchmark comparing the performance in windows and linux.  Does anyone know how to make it work?

I also tried some 3rd party modified version of the demo that I found somewhere on the forum (don't remember the URL right off), but that one seems to be incapable of running the demos from the original q3demo distribution.  To make it even better, the readme references this problem had has half the instructions for fixing it in there.  If anyone happens to know about fixing *that* quake version I'd even be willing to work with that one instead.

If anyone knows how exactly to make the q3demo go I'd really appreciate the help!

---

### Post by hw-tph on 2006-04-13
First off, what kind of graphics card do you have? In order to enable hardware acceleration for current ATI and nvidia cards you will need to install the non-free binary drivers from your supplier. There are excellent docs on how to do this in the [wiki](http://wiki.ubuntu.com).


Håkan

---

### Post by El Rey de Todo on 2006-04-13
That's probably my problem right there.  I've got a radeon mobility 9200 but I was using the radeon driver b/c every time I've tried using fglrx lately the screen freezes completely while I'm still able to control the computer with the keyboard.  The screen turns a dark color with some green and purple spots and then over a period of about 15 seconds turns incrementally to almost white.  It's really bizzar.

Why am I able to get the other one (from [http://www.icculus.org/quake3/](http://www.icculus.org/quake3/)) to work with radeon?  It's probably part of the modification they made to the code I guess, but some other mod they did caused the pak files to be incompatible :(

I guess I'll try making fglrx work again (it did work several months ago but I switched to radeon and it hasn't worked again since).  But if anyone knows how to make the q3demo pak file work in this icculus build please let me know!

---

### Post by El Rey de Todo on 2006-04-13
I finally managed to get on to the id software ftp server and noticed that the latest demo release was from 99 and the latest q3arena release was from 2003.  So I installed the q3 arena release but it won't start for a different reason.  It's complaining about not being able to find default.cfg, a file which doesn't seem to exist anywhere in the installation directory.

Has anyone EVER gotten quake 3 for linux working? is it just a lost cause?

---

