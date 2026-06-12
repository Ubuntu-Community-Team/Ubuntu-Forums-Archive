---
title: "Hard drive test"
date: 2009-05-22
forum: General Help
---

### Post by grantemsley on 2009-05-22
Is there a program or command to run a full hard drive test, similar to what the Seagate or WD's windows tools do?

My drives are starting to get up there in age, so I'd like to scan them for bad sectors once in awhile.  SMART isn't always as smart as it thinks it is.

---

### Post by wirelessmonkey on 2009-05-22
FSCK, specifically e2fsck will do what you want using the badblocks program, on a per partition basis, assuming your partitions are ext2 or 3.
First unmount the disk to check, or boot from the Live CD, then:
```

sudo e2fsck -c /dev/sdaX

```
Where sda could be replaced with whichever drive letter, and X replaced with the partition number.

---

### Post by 73ckn797 on 2009-05-22
In Synaptic down load "smartmontools". Also go to the Smartmon web site ([http://gsmartcontrol.berlios.de/](http://gsmartcontrol.berlios.de/)) and download and install "gsmartcontrol_0.8.4-1~getdeb1_amd64.deb" (for the 64bit system, it does have one for 32bit) and install using "Gdebi Package Installer". If it (Gdebi) is not listed in Applications/System Tools then go to System/Accessories/Main Menu and select it under System Tools.

I just did the same and confirmed a hard rive starting to fail. There are several drive tests it will perform in a graphical menu that did the trick.

---

