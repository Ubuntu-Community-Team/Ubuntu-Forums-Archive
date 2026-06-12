---
title: "Can't boot into Windows after reinstalling Grub."
date: 2006-07-16
forum: Desktop Environments
---

### Post by Shoeberto on 2006-07-16
I installed Ubuntu on the second partition of a drive, and then later on installed Windows on the fourth.  Obviously this overwrote the boot sector, but the Windows boot loader showed an unknown OS, which I assumed it would be able to boot into.  I didn't use Ubuntu for a while until tonight, when it wouldn't load.  I figured out how to reinstall Grub and get it working, so I am able to boot into Ubuntu.  However, I cannot get back into XP.

Some items of interest:
```
title		Windows 95/98/NT/2000
rootnoverify	(hd0,3)
makeactive
chainloader	+1
```
The XP entry into my menu.lst
```
omitting empty partition (5)

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        7220    57994618+  1c  Hidden W95 FAT32 (LBA)
/dev/hdc2            7221       14142    55600965   83  Linux
/dev/hdc3           14143       19929    46484077+   5  Extended
/dev/hdc4   *       14440       19929    44098393+   7  HPFS/NTFS
/dev/hdc5           14143       14439     2385589+  82  Linux swap / Solaris

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        9729    78148161    7  HPFS/NTFS

```
My fdisk -l.

Like I said, it won't boot into Windows at all.  I've never had problems with grub and booting into XP.  I reckon it has to do with the install being on a strange partition.

I've tried using the recovery console to do both fixboot and fixmbr, but neither of those work.  I really don't want to have to reinstall XP again just a week after doing it, and it doesn't seem like I should have to.  Is there anything you guys can suggest?  Thanks in advance.

---

### Post by krazykirk on 2006-07-16
Hmm... my grub thing for my XP partition says:

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1 
```

Maybe you should try putting the "savedefault" thing in there and see what happens.

---

### Post by [S|G] on 2006-07-16
Note that your configuration file states
```
rootnoverify	(hd0,3)
```
While your hard drive is in fact /dev/hdc (secondary master). Just change the rootnoverify to (hd2,3) and it should work.

---

### Post by cotcot on 2006-07-16
Windows does not like to be on another partition than the first, that is for sure. My guess this is the problem. It should be on this hidden partition. I do not have a solution. But maybe you could google on how to boot windows on a second, third, ... partition.

---

### Post by Shoeberto on 2006-07-16
Wouldn't that be (hd1,3), since it starts from 0?  Just to make sure.

Also, my Ubuntu entries in the menu.lst are booting from (hd0,1), but are on the same drive.  Does it do something special to allow itself to boot differently?

---

### Post by [S|G] on 2006-07-16
(hd1,3) would be /dev/hdb4 and not /dev/hdc4

---

