---
title: "Xubuntu 12.04 - ENE tech SD Card Reader - Emachines e350"
date: 2013-01-28
forum: Desktop Environments
---

### Post by Knyquist on 2013-01-28
Hello!

I'm having problems in getting the SD card reader (ENE tech) to work in an Emachines e350 under Xubuntu 12.04 fresh install..

The bug was reported on the launchpad at the address: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277)

There were also many fixes proposed which involved the installation of the keucr module but with newer kernels the source code doesn't seem to work anymore (some defines are missing): it doesn't compile.

There was also a thread (recently closed because old) about how to solve this problem:
[http://ubuntuforums.org/showthread.php?p=10909469](http://ubuntuforums.org/showthread.php?p=10909469)
but of course it refers to older kernels

Thus,  I'm opening this one, hoping  to find some support from the community.



What I have tried till now is to compile the module by adding brutally the missing defines to the usb.h header in the files of the keucr module, but although it won't show any error while compiling, the module won't work.
I had the same problem long time ago when I was using Ubuntu 10.10. At that time I solved the problem by upgrading the kernel to the 2.38 version. This could hopefully help to find a solution.

Thanks and regards!

---

### Post by Knyquist on 2013-01-30
I have news.

In **3.2.0-36-generic** kernel the module used to access the SD card (model **ENE Technology UB6250**) is the **ums_eneub6250**.

I've realized it works with SD card (old card) while it doesn't with SDHC ones.
With the previous distribution Maverick 10.10 (kernel 2.6.38) even the SDCH card worked without any issue.

This time I tried something weird. I don't know whether this actually could have had causes, but with Windows 7 I deleted the .trash folder in the SDHC card and than I plugged it back to xubuntu. It worked fine the first time but than, when I tried to unplug/replug it in, nothing happened as usual.

From a more scientific point of view, the command "lsubs" usually doesn't show the Card Reader, while if the SD card is inside it shows up. Nothing happens when using an SDHC.

---

