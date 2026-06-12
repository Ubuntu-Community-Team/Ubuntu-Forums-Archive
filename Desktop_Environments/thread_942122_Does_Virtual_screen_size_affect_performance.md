---
title: "Does Virtual screen size affect performance?"
date: 2008-10-08
forum: Desktop Environments
---

### Post by zggame on 2008-10-08
I upgraded to ubuntu 8.10 beta from 8.0.4 yesterday, and everything is updated.  It is 32bit version on acer 5620Z, Intel Pentium-dual T2370(1.7G), 1x2G DDR2 667, GMA 3100 (960GL), Tungsten 1.4 Mesa 7.2.  I set a virtual display 3000x1050 in xorg.conf to use it with a widescreen LCD (1680x1050) in VGA port with the laptop's own (1280x800). First of all, I cannot get 1680x1050 on VGA, the highest I can get is 1400x1050.  But also I found "X:" often taking as much as 30%+ CPU, and constantly hovering around 15% (according htop).   I used to have no such high CPU usage in "X:" when I used 8.0.4.  I commented virtual statement in xorg.conf and restarted X.  The virtual screen becomes 1280x1280. CPU usage of "X:"  seemed lower to 15% occasionally and <10% most of the time. But the virtual memory only changed from 400+M to 350M.   

It seems original large virtual screen hinder the performance quite a bit.   I had no idea how X works in this area and did not systematically testing this assumption.  Is it so?    I would need the large virtual screen occasionally to use an external VGA but most time I only use laptop's own.  So it will be convenient to keep the virtual screen there all the time, otherwise, I have to change the xorg.conf whenever I need it. 

Any suggestion. :confused:

---

