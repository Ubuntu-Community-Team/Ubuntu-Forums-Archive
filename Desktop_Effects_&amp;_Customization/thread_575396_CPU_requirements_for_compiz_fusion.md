---
title: "CPU requirements for compiz fusion?"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by patrickthebold on 2007-10-14
So I'm excited about gutsy and want the desktop effects.   My computer is old and I know at the very least that I will need a new video card.  I was wondering anyone has experience running compiz fusion with a slow processor.  Mines 800Mhz.

---

### Post by FredB on 2007-10-14
The most important is your graphic card. I run it with a Sempron 3100+ / GeForce FX 5200 - 128 Mb.

You can set the level of effect. But I think if you're not having a good graphic card, you'll not have compiz on it.

---

### Post by avik on 2007-10-14
Yeah, the graphics card is the most important.  On my system, the processor is barely affected by Compiz-Fusion, so I'm assuming all the load goes to the GPU.  You don't need a great graphics card, but you might be able to run it on your computer with a better graphics card.  It's worth a shot.

---

### Post by patrickthebold on 2007-10-14
Thanks guys!  I just order a cheap video card, Geforce fx5200.  I'll let you guys now how it goes next weekend.

---

### Post by patrickthebold on 2007-10-22
The results so far:

I got a cheap GeForce 5200, and did the gutsy upgrade.  The open source nv drivers did not work at all, so I had to do a text install and then install nvidia-glx-new from the command line.  

Things still weren't perfect.  I had no cursor, desktop effects were shaky, gxine would always crash the X server, and I had no virtual terminals... the Alt+Ctrl+F3 things.  Adding Option "HWCursor" "off" gave me a cursor, I turned off desktop effects, and downgraded to nvidia-glx, and things are ok.  Still no Virtual Terminals and I can't really find any info.  I tried playing with the framebuffer modules but no luck.  I definitely had Virtual terminals before the nvidia video driver was installed.  

I'm a little disappointed.  I didn't really expect the desktop effects to work well, but the fact that I had to to a text install because the open source drivers didn't work seems bad.

I feel like with some more playing I might be able to get everything to work nicely.  If anyone has any leads on the terminal thing, I would appreciate it.

---

### Post by envying on 2007-10-23
I have an old comp.  
AMD Athlon 1GHz
512MB PC133 SDRAM
Geforce 2 MX400 32MB
Shuttle K11T MOBO, VIA Chipset (I guess)
SB Live 16bit Audio
IBM 40GB IDE HD
15" AOC CRT

Just had my ubuntu installed yesterday, it's a very cool system, but I am not sure if I can have compiz activated, Anybody can give me a help, first time on Ubuntu (7.1)

thanks in advance!:guitar:

---

### Post by envying on 2007-10-23
bump!:popcorn:

---

### Post by patrickthebold on 2007-10-23
Why don't you try it and see if it works.  Compiz is installed by default (7.10), so if you didn't do anything it should be running.

On my computer the desktop effects were to screwy to be usable.  I'm not sure if for me it was a hardware or software issue, as I am having issues with both drivers nv and nvidia.

---

