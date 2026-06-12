---
title: "How can I see the version of ATI graphics driver version? (8.0.4)"
date: 2008-12-14
forum: General Help
---

### Post by gotix on 2008-12-14
I have Ubuntu 8.0.4, on a machine with an ATI X550.
lspci says:
02:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
02:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]

It has the default Ubuntu drivers.

Question: how can I see what version number of drivers is installed?
And what is the drivers package name? Is this one? : linux-restricted-modules-2.6.24-19-generic

Is this the right way to update drivers?
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

(as [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) says)

thanks

---

### Post by jpkotta on 2008-12-15
Try ```
atigetsysteminfo.sh
``` and ```
dpkg -l "*fglrx*" | grep ^i
``` for a list of installed packages.  Honestly I can't remember what package it's in because half the time I end up installing it manually and the other half they change the official package.

---

