---
title: "xubuntu setting up your X - display"
date: 2010-11-09
forum: Desktop Environments
---

### Post by metallica1973 on 2010-11-09
I noticed that after certain installations in Xubuntu/Ubuntu and many other distro, some of the times the distro will load the correct video module and resolution for the most part but in others we are stuck in messing with the xorg.conf file. I have observer that in the newer distros they dont use xorg.conf anymore and have steered toward xrandr. My question is:

1 - If after an initial install you have no video and you know what hardware you have, how would you use xrandr to configure the machine to boot with the correct resolution and setting?

2 - I also read that you can still use the xorg.conf, would this still be the standard method of setup?

---

### Post by Viciou§ on 2010-11-10
So far I have only had problems with supported resolutions not being detected. This is because of faulty EDID information.
I always create a xorg.conf file if video isn't working.
Correct me if I'm wrong but xrandr is only used for resolution changing and such?

So:
1 - you don't. Though you can test modelines to see if they display correctly on your monitor.
2 - yes

---

