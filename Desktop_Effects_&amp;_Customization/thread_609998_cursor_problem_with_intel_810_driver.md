---
title: "cursor problem with intel 810 driver"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by CatKiller on 2007-11-11
I've just installed Ubuntu Gutsy on a resurrected computer for the other half. After dropping the colour depth to 16 bits I get direct rendering (hooray!) so I've tried enabling the "Desktop Effects", even though it's just some ancient integrated thing*. Unfortunately, although most things are still nicely snappy with Compiz Fusion running, I've got a problem

When windows are closed - including tooltips - a little square gets left behind where the mouse pointer was. I'm guessing that it's some kind of hardware cursor problem, but I've got no idea what sort. Also, resize operations (drawing a box on the desktop, for example) are really slow. I suspect that this might be related.

So has anyone else come across a hardware cursor problem with CF with these Intel graphics? It only does it with CF turned on - normal Metacity is fine. Did you fix it, and if so, how?

Ta.

* In particular: Intel Corporation 82810 DC-100 (CGC) Chipset Graphics Controller (rev 02)

---

### Post by westbywest on 2007-12-27
I experience similar problems using the mouse cursor with compiz, especially when slowly dragging windows up or down.  I attach a screenshot.  Does this look similar to your problem?

My specs:
HP NW8240 Laptop
ATI Technologies Inc Radeon Mobility X700 (PCIE)
Ubuntu v7.10
compiz 0.6.0+git20071008-0ubuntu1.1
libgl1-mesa-glx v7.0.1-1ubuntu3
libgl1-mesa-dri v7.0.1-1ubuntu3
linux-image v2.6.22-14-pentm+suspend2 (tuxonice patch, compiled for Pentium M)
xserver-xorg-video-ati v6.7.197-1ubuntu1~tormod (patched to fix problem with LCD display sync)
xserver-xorg v7.2-5ubuntu13

---

