---
title: "Not able to re-install grub2, can't mount partition"
date: 2010-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kmels on 2010-04-20
Hi, this morning Grub 2 couldn't boot, displaying the message: File not found and the grub rescue prompt.

I tried to follow the instructions here:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

But, when doing
```
mount /dev/sda1 /mnt
```
I'm asked for a file system type.

When specifying it, (tried with ext3 and ext4), it says it can't recognize the fs.

$fdisk -l

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30393039

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14222   114238183+  83  Linux
/dev/sda2           14223       14593     2980057+   5  Extended
/dev/sda5           14223       14593     2980026   82  Linux swap / Solaris

```


Also, doing $fsck /dev/sda1 outputs
```
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

Any help appreciated, I wouldn't mind re-installing Ubuntu but I'd like to recover my files. Thanks.

---

### Post by Kmels on 2010-04-20
Solved it, hard drive was damaged, fixed.

---

