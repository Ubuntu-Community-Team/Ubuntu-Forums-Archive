---
title: "Dual booting Xp SP3 and Ubuntu 8.04"
date: 2009-02-06
forum: General Help
---

### Post by yusuo85 on 2009-02-06
Ok I have two sata drives, I installed XP and Ubuntu, now I could access the windows xp partition the first few times but after about 5 boots it suddenly popped up saying NTLDR is missing press Ctrl+Alt+del to reboot.
I have no idea why its doing this. I used the xp disk to restore the NTLDR which just repaired the xp boot loader upon installing the grub loader I had the same problem.
Fdisk shows 

yusuo@media:~$ sudo fdisk -l
[sudo] password for yusuo: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c3accd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb753b753

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3187    25599546    7  HPFS/NTFS <---- XP
/dev/sdb2            3188        6329    25238115   83  Linux <----- 8.04
/dev/sdb3            6330        6402      586372+  82  Linux swap / Solaris
/dev/sdb4            6403       30401   192771967+   7  HPFS/NTFS 

menu.lst shows

## ## End Default Options ##

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=38f96165-8c5b-4a8c-adf4-2d35b35eea64 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=38f96165-8c5b-4a8c-adf4-2d35b35eea64 ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

any ideas????

---

### Post by _sleeper on 2009-02-06
the ntldr missing message is  something that microsoft never could actually tell why is happening. but i guess, if you have ubuntu and xp into different disks,  that might cause the problem. grub and windows bootloader are installed into the different disks as well, so that's the case. if you want to boot on xp, you could change from the bios settings the boot priority.

EDIT: i just noticed that on your fdisk output it shows that xp and ubuntu are on the same disk (sdb -> hd1), but on the menu.lst it shows that it is on (sda -> hd0). so, if you change on your menu.lst list the **hd0,0** into **hd1,0 **should do the trick.

---

### Post by zvacet on 2009-02-06
Maybe [this]("http://tinyempire.com/notes/ntldrismissing.htm") will be some help to you.

---

### Post by yusuo85 on 2009-02-06
thanks guys ill give that a try now

---

### Post by caljohnsmith on 2009-02-06
It looks to me like your Windows entry in your Grub's menu.lst is not correct, and you are actually booting your sda1 partition rather than your sdb1 Windows partition. Thus you could get a "NTLDR missing error." How about trying this entry instead:
```

title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Let me know if that works or not, and we can work from there if necessary.

---

