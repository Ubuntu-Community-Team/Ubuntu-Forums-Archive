---
title: "Cinnamon running in software rendering mode while Unity and Gnome work fine"
date: 2013-12-15
forum: Desktop Environments
---

### Post by castillojdavid on 2013-12-15
I'm running Ubuntu 12.04 32bit with Intel Atom CPU N2800 and GMA3600 graphics chipset (Lenovo S110). I have the drivers "Intel Cedarview graphics driver" and "drm driver for the Intel GMA500" both "activated and currently in use" in the Additional Drivers window. Unity and Gnome work perfect, but when logging in with Cinnamon it runs in software rendering mode, not recognizing the graphics driver.


This Intel graphics chipset have a really bad support for linux and the proprietary and outdated driver will only work with this kernel version ([https://wiki.archlinux.org/index.php/Intel_GMA3600](https://wiki.archlinux.org/index.php/Intel_GMA3600)).


Thanks in advance, any help is really appreciated.

---

### Post by castillojdavid on 2013-12-16
Cinnamon won't work with this gpu. I solved the problem installing Linux Mint 13 Maya MATE edition 32bit, which is based on Ubuntu 12.04 and is also LTS with support till 2017. Or maybe you can try MATE under Ubuntu 12.04?


I, then, updated the system and installed cedarview-graphics-driver and cedarview-drm and the system runs just great.


MATE is very similar to Cinnamon and is really customizable. Give it a try, or stay with Gnome or another DE if you don't like it. You can also backport MATE 1.6 to Linux Mint 13 as described here: [http://blog.linuxmint.com/?p=2524](http://blog.linuxmint.com/?p=2524)

---

