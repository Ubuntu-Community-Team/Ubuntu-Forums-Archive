---
title: "Kwin Tearing on Kubuntu 14.04"
date: 2014-07-13
forum: Desktop Environments
---

### Post by will45 on 2014-07-13
Hey guys!

I'm new to the forums here, and new to Ubuntu (I am used to Arch, CRUX, stuff like that) and I just built a new PC 3 days ago. I have installed Kubuntu 14.04 after using Mageia KDE and it's great so far. I am just annoyed with the tearing with my Nvidia card. Is there any way I can get it to not tear as much or something? My graphics card is a MSi GeForce GT N210 using the 331.38 driver.

Thanks,

Will.

EDIT: FACEPALM! SO quickly after posting... Someone on Cup of Linux found [https://wiki.archlinux.org/index.php/NVIDIA#Avoid_screen_tearing_in_KDE_.28KWin.29](https://wiki.archlinux.org/index.php/NVIDIA#Avoid_screen_tearing_in_KDE_.28KWin.29). I added the 2 lins into /etc/profile.d/kwin.sh, and everything worked fine after reboot. Sorry if I wasted time.

---

