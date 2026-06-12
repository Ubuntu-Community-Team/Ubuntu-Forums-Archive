---
title: "Quake 4 Jumpy Movement"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by zachtib on 2007-08-27
just bought quake 4 and set it up on feisty amd64.  it runs fine, but my movement is jumpy.  my character will take a few steps, then stop for a split second and then keep going, while i've got the 'W' key held down.  i'm wondering if it's related to my wireless keyboard, could the wireless signal be flickering every few seconds or something?  what are your thoughts?

---

### Post by zachtib on 2007-08-28
*bump*

anyone?  I seem to remember having the same problem in Doom 3

---

### Post by boho103 on 2008-08-19
> **zachtib said:**
> *bump*

anyone?  I seem to remember having the same problem in Doom 3

triple bump
old thread
experiencing it in both doom 3 and quake 4
any fixes yettt

---

### Post by Brebs on 2008-08-19
Here's [some suggestions](http://forums.gentoo.org/viewtopic.php?p=4014247#4014247).

Doom3 & Quake4 are only *properly* smooth when they are locked to 60 frames per second with:
```
set com_fixedtic 1
set com_syncgameframe 1
```
However, that requires a powerful graphics card, otherwise the game will run in slow-mo.

Also, you can probably reduce the jerkiness by recompiling the kernel, removing its advanced attempts at power-saving and CPU scheduling - it [worked for me](http://forums.gentoo.org/viewtopic-t-701119.html). It needs experimentation, to see what works best for your setup.

---

### Post by CHaoSlayeR on 2008-12-16
I also have that issue.

But I do experience some other strangeness. Quake 4 runs worse when another user has logged out and I have logged in. In that case also glxgears shows me that every 10-15 seconds there is a major breakdown in speed (usually I have around 2800 FPS) and it reduces to around 1200 or less and then up again. Doing so very regularly.

After seeing that I have experienced that rebooting the computer, logging in and playing right away gives me the best performance. Although I have check with top and ps previously if there is anything running from an old user that might interfere I still experience the very regular frame rate breakdown. I've made some screenshots from a scene showing off the lowest and the highest frame rate I was able to catch within some seconds without any movement, just standing still.

Lowest FPS:
[IMG]http://www.chaoslayer.de/shared/quake4linux/fps_low.jpg[/IMG]

Highest FPS:
[IMG]http://www.chaoslayer.de/shared/quake4linux/fps_high.jpg[/IMG]

As I said before I started the game I made sure that there is no other processes that cause much CPU time. In addition I turned SMP on.

My machine:
[LIST]
[*]AMD X2 4400+
[*]AMD/ATI Radeon HD2400 PRO (256MB)
[*]2 GB DDR2 RAM
[/LIST]

After some time of playing it well... mostly get better... somehow... without a message on the console. In addition to this issue I experience very heavy flicker in the first ~30 seconds the game is started. Anyone knows about a fix for that? Although that might be caused by one of the configuration changes I made to Quake4config.cfg.


Regards,

C]-[aoZ

---

