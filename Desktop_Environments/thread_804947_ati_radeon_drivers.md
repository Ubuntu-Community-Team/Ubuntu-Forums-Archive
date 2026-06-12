---
title: "ati radeon drivers"
date: 2008-05-23
forum: Desktop Environments
---

### Post by shardtard on 2008-05-23
I can't seem to get my ati drivers to work..I have a ati radeon hd 2400 pro. Tried to search the forums but could only find help on other ati models

Shardtard

---

### Post by Cygoku on 2008-05-23
If you are Hardy Heron, enable the hardy proposed repository and install Envy (gtk and common).  The rest is obvious!

Cygoku

---

### Post by guildofghostwriters on 2008-05-23
You might not need to use Envy and from my own experience I would only try Envy as a last resort.

First of all, go to system-admin-hardware drivers (if it's not Hardy it might be system-admin-restricted drivers or something along those lines). If there's a driver and your card listed there, click to enable and restart. I have a (different) radeon card and that's all I needed to do with Hardy.

If it's not listed, follow these instructions here, use the second method - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you have problems editing xorg.conf near the end of the guide, try sudo nano instead of sudo gedit. For some reason, when I followed this guide it wouldn't let me launch gedit but I could do it in terminal with nano.

One thing that repeatedly loused up my attempts to install ati drivers in Ubuntu was having two monitors connected. For some reason, if I have a second monitor attached, it boots to a white screen when I reboot, or low graphics mode, and in the end I've just had to forget dual head for now. So if you keep having problems and there's a second monitor connected, disconnect it and try to reboot.

Good luck!

---

### Post by TimGS on 2008-05-23
EnvyNG worked for me
[http://ubuntuforums.org/showthread.php?t=792988&highlight=hardy+ati](http://ubuntuforums.org/showthread.php?t=792988&highlight=hardy+ati)

---

