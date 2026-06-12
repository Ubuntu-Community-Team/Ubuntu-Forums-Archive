---
title: "ATI(fglrx) and XGL Problems"
date: 2007-01-16
forum: Desktop Environments
---

### Post by joeroot on 2007-01-16
Hi,

I've just installed beryl on xgl and I have been having several problems with my ATI Radeon 9000.

Firstly whenever I boot into xgl, the screen goes all fuzzy, similar to tv noise, and the cursor becomes an x. After ubuntu has finished loading the desktop however tis goes away.

Secondly, when i go to system --> quit, the only option available is the hibernate option, and then the various log out options, but there is no shut down option.

Any help regarding this matter really would be greatly appreciated.

Thanks,

joe

---

### Post by mysticmarks on 2007-01-16
you need some editing in your xorg.conf file. the driver you're using does not support the 3d desktops. You need the open source driver. Read this---> [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

ps- be very careful! adding the lines to xorg.conf. I haven't been able to use the Option     "XAANoOffscreenpixmaps" without screwing up my drivers. I then had to use vim to reload my conf file. You may as well _write down_ this info too in case you do what i did. It will get you back up so you can edit the file over.

sudo dpkg-reconfigure -phigh xserver-xorg

Good Luck!

---

