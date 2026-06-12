---
title: "Screensavers Freeze but not computer..."
date: 2005-12-25
forum: General Help
---

### Post by matthinckley on 2005-12-25
OK I have searched around the forum and I have reinstalled a few times..

Everything I find in search is the screensavers lock up the whole computer but in my case just the screensaver freezes.. pressing any key or mouse button exits the screensaver like normal.. but it doesn't seem like much of a screensaver when about 5 minutes after the screensaver starts it freezes and just leaves a static image on my screen.. doesn't matter which screensaver it is.

I can't find any screensaver logs? if there are any, but this is something I really would like to get fixed.. I leave my computer on all the time and sometimes leave my house for days at a time.. I know I can just change it to blank the screen and then it wouldn't matter but I would like to get this fixed...  

I am using an ATI Radeon 9600 PRO 128 video card and here is my fglrxinfo output

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5519 (X4.3.0-8.20.8)

```

thanks ahead for any help

Matt

---

### Post by siorai on 2005-12-25
Actually, I have the same problem with any of the accelerated screensavers. It sucks too because the one that I really want to use, XAnalogTV won't work. For now I'm using the BSOD saver since it's definitely not accelerated.

I'm running an Nvidia 6800 with the latest drivers and acceleration is definitely working, just not with the screensavers.

---

### Post by matthinckley on 2005-12-26
yeah XAnalogTV is the one I like too.  I'm wondering if nobody else has this problem.. I thought it might be something to do with my hardware, but strange that we have the same problem since you have nVidia and I have ATI..

---

### Post by earcaraxe on 2006-03-21
I have this same problem as well. I'm running an ATI x800 GTO2 that i rewrote the bios on to make it think its an x850 (unlocked 4 pixel pipelines that were on the card). Everything else seems to run fine except when I run accelerated screensavers (flurry is my favorite) after about 5 minutes it freezes and I have all of the same symptoms as you.

I reinstalled fgrlx and this problem hasn't gone away.

---

### Post by matthinckley on 2006-04-29
Dapper has fixed this problem

---

### Post by nzmoose on 2006-05-11
one more for the heap. ive got dual view on a GF 6600 one freezes then the other about 10 seconds later

---

