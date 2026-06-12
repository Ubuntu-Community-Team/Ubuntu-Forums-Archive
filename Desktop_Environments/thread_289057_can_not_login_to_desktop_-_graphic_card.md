---
title: "can not login to desktop - graphic card"
date: 2006-10-30
forum: Desktop Environments
---

### Post by smithveg on 2006-10-30
hello,

before i update the packages, i still can play the games, but i can not plan the games anymore after i had upgrade the package, i my assumu that the graphic card driver was missing. So i just try to reinstall the graphic card driver. BUT after i install then i restart. I can not login to the desktop anymore. Can anyone tell me how to change the graphic settin to the default in console 1/2/3/4/5/6.

If i'm right, i think i should change at

sudo gedit /etc/default/linux-restricted-modules-common

BUT i seems can not open this file in console, can someone teach what to do now?
Thanks

---

### Post by lazyart on 2006-10-30
are you stuck at the command line?  Log in, then type:

sudo dpkg-reconfigure xserver-xorg

Walk through and set up your enviroment and you should have your desktop back.

---

