---
title: "Ubuntu, Vista, Media Direct partition dramas"
date: 2008-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jooo on 2008-05-05
Ok, I'm really not sure if i should be asking a windows forum, a dell forum, or here...

First some background:

I installed Ubuntu, Vista, and Media direct. Everything worked fine. Then I tried installing additional codecs for media direct (which worked the previous time I've tried it), but this time it just bsod's on boot...

I figured ok... lets just hose the media direct partition and install mythbuntu on it and see what happens...

Here's when I realised that things have gone horribly wrong. When trying to check out my partitions, gparted reports the entire drive as being unallocated. (the drive is ment to have 6 partitions on it)

Vista won't boot. It attempts to boot, but then starts booting media direct, then bsods.

Ubuntu however works as per normal. It does however report 2 media direct partitions (and it appears to mount the same partition twice)

Now I'd like to fix this problem, but i have no idea where to start. I'm guessing first thing would be to fix the partition issue... how would i go about doing that?

sudo fdisk -l from within ubuntu (not live cd) gives:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38652       38913     2104483+   c  W95 FAT32 (LBA)
/dev/sda2   *           7       30684   246421035    7  HPFS/NTFS
/dev/sda3           30685       38913    66099442+   f  W95 Ext'd (LBA)
/dev/sda5           38652       38913     2104483+  dd  Unknown
/dev/sda6           30685       35788    40997817   83  Linux
/dev/sda7           35789       37655    14996646   83  Linux
/dev/sda8           37656       38651     8000338+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

I think sda1 is ment to be the dell utility partition which is ment to be something like 60mb, but here it seems to be the same size as the media direct partition (sda5 i think).

Thanks!

---

### Post by jooo on 2008-05-06
Just an update, after a lot more searching and experimenting, I managed to fix my own problem by booting with a Gparted live cd and using ```
testdisk
```.

After some messing around with that, i can see my partitions fine with gparted.

Rebooting gives a grub 17 error which was resolved after searching the forum.

Hopefully this info might be useful for any newbs like me.

---

