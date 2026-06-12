---
title: "Random Hardlocks after installing 6.06"
date: 2006-06-23
forum: Desktop Environments
---

### Post by jlrussell on 2006-06-23
After installing Ubuntu 6.06 my machine has started to randomly hard lock for no apparent reason that I can tell.  I've installed the system twice, once using the install option on the live CD and the other in text mode.  Ordinarily I would say that any hardlock is usually a hardware problem, but the machine did not exhibit this behavior before installing 6.06 (previously had Ubuntu 5) nor did it appear in XP.  Before leaving for work today I left the machine at the log on screen and it was fine when I got home.

I have a relatively standard machine...  Pentium IV, 2 GB RAM, SATA HDD, and a Radeon 9700 video card.

I know my way around the system well enough to get by, but I honestly have no idea where to go to begin to troubleshoot this and isolate the problem.  Anyone have any advise on this?

---

### Post by jlrussell on 2006-06-24
I don't know why, but I had a hunch that it might have something to do with the video.  So I did some research and ended up installing the non-open source drivers for my video card.  Since then the hardlocks have become more manageable (every few hours vs. every 10 or 15 minutes) but they're still occuring.  

Are there any modules that might be causing the locks?  Right now, the following modules are being loaded in xorg.conf:

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Thanks for any help!

---

### Post by clintonthegeek on 2006-06-24
Hmm... come join us in [this]("http://www.ubuntuforums.org/showthread.php?t=193283") thread over here... a bunch of people (including myself) are having the same problem.

-Clinton

---

