---
title: "automatically mounting removable devices when they are plugged"
date: 2009-05-26
forum: General Help
---

### Post by netimen on 2009-05-26
I have found many threads on this problem but still no solution.

I want the following behavior when I plug a device (USB stick or CD disk):

1. it should be mounted automatically for me. Now it isn't, though it appears in fdisk -l output:
```
Disk /dev/sdd: 8006 MB, 8006926336 bytes
16 heads, 32 sectors/track, 30544 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x9b12d290

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          16       30544     7815232    b  W95 FAT32
```
and if I mount it manually, all goes OK

2. if I mount manually my CD disk and then press the eject button on my drive nothing happens until I manually unmount the drive. But I want it to open immediately

All this worked for me in 8.10, and broke with the upgrade.

my fstab entries
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc1 /media/usb vfat noexec,codepage=866,utf8,nosuid,nodev,quiet,uid=1000,gid=1000,umask=077,user 0 0

```

---

