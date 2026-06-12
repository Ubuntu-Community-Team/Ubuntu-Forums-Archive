---
title: "Kubuntu consuming 982 MB of RAM !"
date: 2007-01-28
forum: Desktop Environments
---

### Post by Shinok on 2007-01-28
Hey, i'm kinda new to Linux so i decided to try Kubuntu since i like KDE interface better... i've installed all i needed and started to use it. It normally used 500 - 600 MB of RAM but today i felt like it was slower, i checked the Performance Monitor and i was surprised, with only running firefox, azureus and aMSN it was using 982 MB of RAM ! :?



Is this normal? i hope not, because then Windows Vista would use less ram than Kubuntu and that would be a shame.




BTW these are my computer specs;


Intel E6600
Asus P5W DH Deluxe
1 GB Corsair XMS2 DDR2 800 @ 1050
Hitachi 400 GB Sata2
XFX Nvidia 7600GT
Sony DVD/CD RW
OCZ ModStream 520W



Cheers !

---

### Post by theslut on 2007-01-28
it's a good thing. It means your RAM is not sitting being wasted by not being used.

Linux uses ram much more efficiently than Windows. I'd only be worried if you were constantly using the linux swap file. Type "top" at a command prompt to monitor it.

Here is mine after a few days of being switched on.

Mem:   2075992k total,  2015148k used,    60844k free,    59276k buffers
Swap:        0k total,        0k used,        0k free,  1330848k cached

I've got 2gb and Linux actually uses it.

---

### Post by Mac_D83 on 2007-02-02
Yes it's quite normal. Linux uses the available RAM for file cache, so your programs starts faster. 
This improves the responsiveness of the system a great deal, making it feel a lot faster. This can
be demonstrated by timing the start-up time of firefox. Close firefox and start it again. Firefox 
should open much faster the second time, because it's read from the cache instead of the slow 
hard drive.

The RAM for the cache will be freed if another program needs more memory, so it's better to use 
the memory for something useful, when it's not needed.

---

