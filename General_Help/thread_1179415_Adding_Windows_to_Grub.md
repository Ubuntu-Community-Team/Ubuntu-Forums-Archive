---
title: "Adding Windows to Grub"
date: 2009-06-05
forum: General Help
---

### Post by MaxRabbit on 2009-06-05
I've been trying to boot Windows from Grub, but I can't figure out what the roots should be. I tried a root of (hd0,0) but that just seems to launch Window's MBR. I've tried other combinations but I just get errors that the partition doesn't exist, etc.

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fe316fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26109   209720511    7  HPFS/NTFS
/dev/sda2           26110       77825   415408770    5  Extended
/dev/sda5           26110       37703    93128773+   7  HPFS/NTFS
/dev/sda6           58496       74711   130254988+   7  HPFS/NTFS
/dev/sda7           74712       74786      602406   82  Linux swap / Solaris
/dev/sda8           74787       77825    24410736   83  Linux
```

SDA1 is Vista. SDA2 is storage (no OS). SDA5 must be my new XP installation. SDA6 is my old Windows XP.

Thank you in advance for your help :)

---

### Post by logos34 on 2009-06-05
The windows boot files have to be on sda1.  So no telling why it doesn't work.

or maybe try 

rootnoverify (hd0,0)

Sometimes [Grub doesn't work well with vista]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20and%20Boot%20Manager").  So what I'd do is restore the windows bootloader and then use [EasyBCD to chainload linux]("http://neosmart.net/wiki/display/EBCD/Linux").

---

### Post by MaxRabbit on 2009-06-05
Thank you very much for the EasyBCD link! That helped me get **everything** working :)

---

### Post by logos34 on 2009-06-05
cool.  enjoy

---

