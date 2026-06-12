---
title: "Help booting from USB"
date: 2009-05-17
forum: General Help
---

### Post by Scripps on 2009-05-17
I've installed 9.04 on a USB flash drive and run it perfectly well on Mac using rEFIt. However, when I try to boot from my HP, I get the following messages:

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
    -Check rootdelay= (did the system wait long enough?)
    -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/df28e9c2-ef56-4b63-bbd3-73e5ac208247 does not exist. Dropping to a shell!

It then proceeds to run BusyBox, but I'm not experienced enough using a command line to know what to do.

Regarding the missing file above, it actually does exist in that location.

Can anyone give me any info on what to do?

---

### Post by Scripps on 2009-05-17
Oh, there's more that I missed. Before that above messages, I get this:

[      2.436078] ata1: softreset failed (device not ready)
[      3.088445] ata2: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

The "missing" file here also exists.

---

### Post by bacardiandwatermelon on 2009-05-17
Sorry I can't really help, but you can also use imagewriter to put an iso on a usb stick.

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by Scripps on 2009-05-17
> **bacardiandwatermelon said:**
> Sorry I can't really help, but you can also use imagewriter to put an iso on a usb stick.

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

Will that be persistent? Also, is there any other particular drawback to booting off an image rather than an actual installation?

---

