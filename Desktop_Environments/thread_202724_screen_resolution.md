---
title: "screen resolution"
date: 2006-06-23
forum: Desktop Environments
---

### Post by macm10 on 2006-06-23
how do i adjust the screen resolution from 1024x768 to 1280x1024 there is no option pased 1024x768 in system>preferences>screen ressolution. i understand that ubuntu comes with tools to make configureing the xserver easy. where are these?

---

### Post by aysiu on 2006-06-23
Ubuntu doesn't come with tools that configure the X server easily. Perhaps you have it confused with SuSE or Mepis.

Still, it can be configured. Try Control-Alt-F1, log in, and ```
sudo dpkg-reconfigure xserver-xorg
``` If that doesn't work, try some methods outlined [here.](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

