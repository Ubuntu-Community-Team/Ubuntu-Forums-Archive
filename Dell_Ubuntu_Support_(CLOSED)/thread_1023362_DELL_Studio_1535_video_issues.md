---
title: "DELL Studio 1535 video issues"
date: 2008-12-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zenlunatic on 2008-12-27
I've got a new Studio 1535.  When I installed ubuntu I got the WSoD.  I had to install in the safe graphics option.  I can only get 800x600 resolution in X. I've tried much everything.  I upgraded to the 9.04 alpha.  I've tried dpkg-reconfigure on X.  I've tried running some script called 915resolution.

Is it possible to get native resolution on the Dell Studio 1535 with intel gm965 integrated graphics?

Oh yeah, I have a AUO LCD.

---

### Post by vigos on 2009-01-14
check to see if you have fglrx installed (thats of course if have ATI radeon card installed) after thats installed you should be able to get more resolutions.

You can check by going System -> Administration -> Hardware Drivers

If ATI is not enabled then click it and enable it, you will probably need a reboot.

The only problem is that now I can only get 1280x800 but can get 1280x1024 on Windows Vista with the same card, so this is what I'm trying to get fixed.

Oopps, sorry just re-read your post you have integrated graphics

---

### Post by Prot on 2009-01-21
[http://ubuntuforums.org/showthread.php?t=892146&highlight=dell+studio+wsod](http://ubuntuforums.org/showthread.php?t=892146&highlight=dell+studio+wsod)

---

