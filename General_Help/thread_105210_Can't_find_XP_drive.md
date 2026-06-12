---
title: "Can't find XP drive"
date: 2005-12-17
forum: General Help
---

### Post by BobInIdaho on 2005-12-17
I have Kubuntu install on its own hard drive and XP on another hard drive in the same system. I am unable to load files off the XP drive. It will not mount.the XP drive no matter what I try. Anyone got any ideas? I'm a total newbie so draw me a picture...:)

---

### Post by mcmuffy on 2005-12-17
The line I have in my /etc/fstab file to access my windows drive is :
/dev/hda5	/media/windows ntfs	user,umask=0	0	0

You would need to change hda5 to whatever drive you use and create a folder called windows (or whatever you put after /media/).

---

### Post by towsonu2003 on 2005-12-17
```
sudo fdisk **-l**
``` may give you an idea about what are your partitions that can be mounted... 

Important note: be careful with fdisk, it's a partition table utility (wrong usage will break stuff)...

here is my fdisk -l ```
Disk /dev/**hda**: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/**hda1**   *           1        2611    20972826    7  HPFS/**NTFS**
/dev/**hda2**            2612        6527    31455270    7  HPFS/**NTFS**
/dev/hda3            6528        9138    20972857+  83  Linux
/dev/hda4            9139       12161    24282247+   5  Extended
/dev/hda5            9139        9399     2096451   82  Linux swap / Solaris
/dev/hda6            9400       12010    20972826   83  Linux
/dev/hda7           12011       12161     1212876    b  W95 FAT32

```

hda is my hard disk and hda1 and hda2 are ntfs partitions.

---

### Post by aysiu on 2005-12-17
See the fourth link in my sig.

---

### Post by BobInIdaho on 2005-12-18
Thanks to all that replied...I'm gonna go try some of that code you provided.:smile:

---

### Post by BobInIdaho on 2005-12-19
Well, it just sorta fixed its self somehow. I never had to do any of the tricks you all suggested. But I thank you just the same. The support here is just awesome.:razz: 

Bob

---

