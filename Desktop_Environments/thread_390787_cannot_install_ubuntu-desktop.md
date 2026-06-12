---
title: "cannot install ubuntu-desktop"
date: 2007-03-22
forum: Desktop Environments
---

### Post by spiderworm on 2007-03-22
Hi,

I was trying to get Beryl working by following the instructions in this popular thread:

[http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

... which states that I must install ubuntu-desktop.  Trouble is, when I try to install it via apt-get, I get the following:

ubuntu-desktop: Depends: xorg but it is not going to be installed

So I try apt-get install xorg

xorg: Depends: libgl1-mesa-glx but it is not going to be installed

OK.... apt-get install libgl1-mesa-glx

... then I get a long list of packages that are going to be removed:

kde-devel
kdebase-dev
kdelibs4-dev
kdemultimedia-dev
kdesdk
kspy
libart1-dev
libavahi-qt3-dev
libgl1-mesa
libgl1-mesa-dev
libgl1-mesa-dri
libglew-dev
libglu1-mesa-dev
libgtkglext1-dev
libkonq4-dev
libopenexr-dev
libqt3-mt-dev
libqt4-dev
libsdl-console-dev
libsdl-gfx1.2-dev
libsdl-image1.2-dev
libsdl-net1.2-dev
libsdl-ttf2.0-dev
libsdl1.2-dev
libsmpeg-dev
x-window-system-core

I really don't want to uninstall x-window-system-core or any of these other packages, do I?

I'm thinking that this problem may exist because this edgy install was originally a dapper install that I dist-upgraded several months ago.

Is it safe to uninstall all these packages just so I can get libgl1-mesa-glx, xorg, and ubuntu-desktop installed?

Thanks,
spidey

---

### Post by aysiu on 2007-03-22
Sounds as if your sources.list is messed up.

[Get a fresh list](http://www.psychocats.net/ubuntu/sources). Then try again: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

