---
title: "AIGLX or XGL"
date: 2007-03-20
forum: Desktop Effects &amp; Customization
---

### Post by gregcoit on 2007-03-20
Hi,

I have a laptop with a NVIDIA Corporation NV17 [GeForce4 420 Go] video card.  I'd like to get beryl working but I have some questions:

My card is supported by either the 96xx nvidia drivers or the 97xx nvidia legacy drivers, but not the regular 97xx drivers.  And it appears that compositing is not supported by the 97xx nvidia legacy drivers (at least for AIGLX).  if so, then I have 2 options:

Stick with the 97xx nvidia legacy drivers and try XGL or backup to the 96xx nvidia drivers and try AIGLX again.

Which have people had success with?

Thanks!

Greg

---

### Post by maxamillion on 2007-03-20
Either will give you success (depending on XGL support for your hardware), I have heard better results with older cards that run AiGLX but that could cause you issues during upgrades and updates so I would actually recommend trying to get XGL functioning with the latest drivers. If not, you can always fall back on AiGLX and the older drivers.

---

### Post by gregcoit on 2007-03-20
Maxamillion - Good advice!

I decided to try the XGL route.  So, I removed AIGLX from my xorg.conf, installed xserver-xgl, created the few necessary files to create a new kdm entry, and viola, it works!  

It's so freaking pretty, smooth, and so far stable!

Thanks!!!

Greg

---

