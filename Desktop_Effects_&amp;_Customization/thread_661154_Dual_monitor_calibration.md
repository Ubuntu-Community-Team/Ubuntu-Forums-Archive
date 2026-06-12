---
title: "Dual monitor calibration"
date: 2008-01-07
forum: Desktop Effects &amp; Customization
---

### Post by jondecker76 on 2008-01-07
I have a dual monitor setup and want to match the appearance of both monitors. Bot monitors are the exact same make and model and bought at the same time. On appears to be much brighter than the other..
I have matched multiple monitors in Windows, but not in Linux. How would I go about getting these 2 monitors to match eachother as close as possible?

thanks,
Jon

---

### Post by BobCFC on 2008-01-08
If you have an NVIDIA graphics card using the proprietary drivers you have a special control panel to setup twinview/gamma etc type:

sudo nvidia-settings

You need to run it as root so that you can press the button to save the changes to xorg.conf file.


Not sure about ATI I think I heard there was a similar program call aticonfig or something?


EDIT: I also had one monitor brighter than the other when two were plugged in I think in the end I turned down the brightness on one then boosted the overall gamma using the above tool.  There's also a digital vibrance slider that had some effect.

---

### Post by jondecker76 on 2008-01-08
I've tried NVidia-settings, and I see the gamma correction, but it has absolutely no tools to help find your correction factor (in Windows,there would be a series of tests you would do suck as picking the darkest "gray" distinguishable from black, lining up red, blue and green swaths so that they look equal along a certain point, etc....) But I can't find ANYTHING like this in Linux.

Anyone else with some ideas?

thanks,
Jon

---

### Post by BungaMan on 2008-01-09
if it is a separate tool that you use on windows, you can try running it in linux with wine.

---

### Post by BobCFC on 2008-01-17
Try asking on the Linux section of the Nvidia forums? 

[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

