---
title: "non-existant old drives still appear mounted"
date: 2011-12-03
forum: Desktop Environments
---

### Post by shkkmo on 2011-12-03
I'm not sure if this is the place for this, but I think that this is a gnome problem

I just finished re-partitioning my Asus eeepc 1000 which has two solid state drives one 8gb and the other 32gb. I removed a partition from each drive and switched which drives my swap was on. Everything worked great and fdisk now shows the current results:

```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000818dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         981     7879851   83  Linux

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004d034

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2862    22985352   83  Linux
/dev/sdb2            2862        3925     8536065    5  Extended
/dev/sdb5            3670        3924     2048287+  82  Linux swap / Solaris
/dev/sdb6            2863        3669     6482196   83  Linux
```

I then went into /ect/fstab to get my new swap file working. While I was there I decided to also try and get my new partitions mounting correctly. Here's how the file looks now:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=682e8df2-0aed-49c7-9e82-65b3372c9739 /home           ext3    defaults        0       2
# /shed was on /dev/sdb6 during installation
UUID=b976eeb5-e466-431a-82ce-821c1cb2cdc2  /shed          ext3    defaults        0       0
# swap was on /dev/sda6 during installation
UUID=09bf9a4b-bac5-4273-9f2d-852d2d2c8bdf none            swap    sw              0       0
```

When I restarted, the old partitions seem somehow to still be mounted in the filesystem. My old partitions were mounted to /shed /outhouse and /sideb and these folders still exist in the root directory. If I try to do anything (create or move a new file or folder) to them it appears that I lack permissions.

I'm clearly missing a step, but I'm at about the limits of my ubuntu knowledge and I would appreciate if anyone can point me in the right direction.

---

### Post by shkkmo on 2011-12-03
I got the old drives to disapear by just deleting them using

sudo rmdir

I removed all of them, including /shed. On restart, only /shed reappeared (yay) but I still don't have permission to access it. I'm guessing I have my options screwed up in the fstab file, but I don't know what to use beside 'default'.

---

