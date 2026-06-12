---
title: "lost file /etc/X11/xorg.conf"
date: 2010-11-18
forum: Desktop Environments
---

### Post by chavitz on 2010-11-18
Dear all,

Unfortunately, I deleted the /etc/X11/xorg.conf file, have no backup, and I'm not able to restore the file even by using the command below (also in recovery mode):
sudo dpkg-reconfigure xserver-xorg

Any suggestions are welcomed!

---

### Post by asmoore82 on 2010-11-18
Modern linux systems no longer need an xorg.conf

Xorg will probe all that it needs on the fly.

The exception is if you need to override Xorg's choice of drivers,
such as for the nvidia proprietary module.

But even then, an extremely minimal Xorg.conf will do -
only specify the values that you absolutely have to.

My previous laptop had Intel Integrated Graphics and needed no xorg.conf at all.
My wife's netbook is based on the nVidia Ion and this is her entire xorg.conf:
```
**$ cat /etc/X11/xorg.conf**

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

---

