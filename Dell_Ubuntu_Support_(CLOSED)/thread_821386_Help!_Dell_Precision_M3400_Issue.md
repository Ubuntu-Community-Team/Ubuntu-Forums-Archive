---
title: "Help! Dell Precision M3400 Issue"
date: 2008-06-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bayesian on 2008-06-07
I recently upgraded from Ubuntu 7.10 to 8.4 and the restricted driver for my NVIDIA FX360M doesn't work any more as the linuz runs in low graphics mode each time I enable it and I have to reset up X.

I am a total novice when it comes to linux so any help would be fantastic!

Cheers

---

### Post by ilexius on 2008-08-05
I expirienced the same problems.
One solution might be to change the following line and install the newest nvidia driver from the Website.
Steps:
open:
"/etc/default/linux-restricted-modules-common" 
find:
&#8216;DISABLED_MODULES=&#8221;"&#8216; (in my case nothing was disabled) 
change it to  
&#8216;DISABLED_MODULES=&#8221;nv&#8221;

Then install the nvidia-driver, just run the nvidia installtool --> this means you now have a recompiled kernel with the nvidia-driver. the consequence you have to recompile your kernel everytime a kernel update is installed.

Greetings,
Thomas

---

### Post by ilexius on 2008-08-06
there is a thread in the NVIDIA forum:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

and for German users you can find a detailed instruction on the installation here:

[http://wiki.ubuntuusers.de/Nvidia-Grafikkarten/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Nvidia-Grafikkarten/Manuelle_Treiberinstallation)

---

