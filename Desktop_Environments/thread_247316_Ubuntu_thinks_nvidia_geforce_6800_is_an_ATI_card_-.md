---
title: "Ubuntu thinks nvidia geforce 6800 is an ATI card - low resolution"
date: 2006-08-30
forum: Desktop Environments
---

### Post by drpolish on 2006-08-30
This is some strange stuff going on.
I boot into ubuntu, and i noticed that my resolution was really really low, around 1024 x 768 on my 1680 x 1050 monitor. openSuse was able to configure the monitor correctly, so i wondered why ubuntu didnt have such a feature. In result, my xorg.conf says that my card is an ATI Radeon and that my screen resolution should be 1024 x 768. I'm able to run ubuntu on my laptop perfectly, and my screen is 21" Gateway monitor. Should i post my xorg.conf? and secondly, is there any automatic xorg configurators? (xconf?)

---

### Post by CatKiller on 2006-08-31
```
sudo dpkg-reconfigure xserver-xorg
``` will reconfigure your X system from scratch. You might want to back up your xorg.conf file first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

