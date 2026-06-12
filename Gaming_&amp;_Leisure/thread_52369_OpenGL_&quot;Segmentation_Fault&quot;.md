---
title: "OpenGL &quot;Segmentation Fault&quot;"
date: 2005-07-27
forum: Gaming &amp; Leisure
---

### Post by neilbain on 2005-07-27
All applications using OpenGL (including glgears and games such as Doom3) report a "segmentation fault".  

I have an AMD Athlon XP 3000+ with a NVIDIA FX 6200 (256MB) with the 7667 nvidia driver.

The graphics card works perfectly in a Windoze XP machine.

I have checked all soname files against the NVIDIA list, removed possible conflicting libs (i think :???: ) and run ldconfig to ensure symlinks are upto date and valid. 

xorg.conf has 'load GLX' enabled and I am set at at 24 bit depth graphics.

Anyone got any ideas where I can look next?????

Newby Neil

---

### Post by shawn on 2005-07-27
Haha, I have spent a long time today trying to fix this, the answer lies (at least for me) in this thread:

[http://ubuntuforums.org/showthread.php?t=37893&page=1&pp=10&highlight=segmentation+nvidia](http://ubuntuforums.org/showthread.php?t=37893&page=1&pp=10&highlight=segmentation+nvidia)

No trouble since then! Good luck!

---

### Post by neilbain on 2005-07-28
[QUOTE=shawn]Haha, I have spent a long time today trying to fix this, the answer lies (at least for me) in this thread:

[http://ubuntuforums.org/showthread.php?t=37893&page=1&pp=10&highlight=segmentation+nvidia](http://ubuntuforums.org/showthread.php?t=37893&page=1&pp=10&highlight=segmentation+nvidia)

No trouble since then! Good luck![/QUOTE]
 Absolutely spot on Shawn... Many thanks.  :-P 

Neil

---

