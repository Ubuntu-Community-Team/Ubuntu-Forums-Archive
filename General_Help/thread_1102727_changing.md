---
title: "changing"
date: 2009-03-21
forum: General Help
---

### Post by abhinav.p on 2009-03-21
i cannot add or delete any file in my partitions after editing fstab as shown below.how can i set read write permissions for non root user?



OUTPUT FOR #ls -l /media


lrwxrwxrwx 1 root root 6 2009-02-13 03:20 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-02-13 03:20 cdrom0
drwxr-xr-x 4 root root 4096 2009-03-05 19:33 disk
drwxr-xr-x 8 root root 16384 1970-01-01 05:30 disk-1
drwxr-xr-x 13 root root 8192 1970-01-01 05:30 disk-2
drwxr-xr-x 5 root root 4096 2008-06-20 22:13 disk-4
drwxr-xr-x 2 root root 4096 2009-02-26 16:47 matlab-temp
drwxr-xr-x 31 root root 16384 1970-01-01 05:30 STUFF









# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=6672cdf4-916a-44d6-a335-e33489a8e0a2 / ext2 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /media/STUFF vfat defaults 0 0
/dev/sda6 /media/disk-1 vfat defaults 0 0
/dev/sda7 /media/disk ext2 defaults 0 0
/dev/sda2 /media/disk-2 vfat defaults 0 0
/dev/sda8 /media/disk-4 ext2 defaults 0 0

---

### Post by dcstar on 2009-03-22
> **abhinav.p said:**
> i cannot add or delete any file in my partitions after editing fstab as shown below.how can i set read write permissions for non root user?
........
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=6672cdf4-916a-44d6-a335-e33489a8e0a2 / ext2 relatime,errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda5 /media/STUFF vfat defaults 0 0
/dev/sda6 /media/disk-1 vfat defaults 0 0
/dev/sda7 /media/disk ext2 defaults 0 0
/dev/sda2 /media/disk-2 vfat defaults 0 0
/dev/sda8 /media/disk-4 ext2 defaults 0 0
```

sudo fdisk -l
``` will tell you what your partitions actually are.

---

### Post by abhinav.p on 2009-03-22
ok here is the output for sudo fdisk -l




Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12        1286    10241437+   c  W95 FAT32 (LBA)
/dev/sda3            1287        2561    10241437+  83  Linux
/dev/sda4            2562       30401   223624800    f  W95 Ext'd (LBA)
/dev/sda5            2562        6385    30716248+   b  W95 FAT32
/dev/sda6            6386       10131    30089713+   b  W95 FAT32
/dev/sda7           10132       15158    40379346   83  Linux
/dev/sda8           15159       22993    62934606   83  Linux
/dev/sda9           22994       30401    59504728+   7  HPFS/NTFS





now how do i change permissions to add or delete files as non root user?

---

