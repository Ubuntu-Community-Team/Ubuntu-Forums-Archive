---
title: "Mupen64 no longer opens"
date: 2011-05-30
forum: Gaming &amp; Leisure
---

### Post by de-dubya on 2011-05-30
Hey guys, first time I've posted so please bear with me if I have missed any forum etiquette..

I have been using Mupen64plus for some time now with no problems at all, then for no reason that I can explain the front end has given up, the only way I can get files to run is by choosing "open with" and even then I have no front end to adjust any settings, it has also removed it self from my drop down.

I have removed and re-installed, downloaded directly from the site but it always ends up with the executable just not doing anything, I have checked my permissions and they are fine, the crazy thing is one morning I was playing, in the evening it gave up..

Using Natty Narwhal 11.04
Acer Aspire 5920
Intel Core 2 Duo T7300
Clock speed 2 GHz
RAM DDR2 667MHz 2048 MB
HDD 5400 RPM 160 GB
Nvidia GeForce 8600 GT
Data bus speed	800 MHz

What have I done?  How do I get it back?

Thanks for any help in advance!

---

### Post by DoktorSeven on 2011-05-30
Did you install one of the 1.99/2.0 versions by chance?  There is no frontend to these included with the base program and you'll have to find one to use.  The best option is to remove it and install a 1.5 version (it should be in the default Universe repositories in Natty).

If you are running 1.5 and you still have this problem you might try removing your configuration from ~/.config/mupen64plus/ and see if that fixes things.

---

### Post by mips on 2011-05-31
> **DoktorSeven said:**
> Did you install one of the 1.99/2.0 versions by chance?  There is no frontend to these included with the base program...

+1

If you have installed 1.99/2.0 then see these two threads for help on setting up a GUI front end:
[http://ubuntuforums.org/showthread.php?t=1686384](http://ubuntuforums.org/showthread.php?t=1686384)
[http://ubuntuforums.org/showthread.php?t=1686297](http://ubuntuforums.org/showthread.php?t=1686297)

---

