---
title: "Question about seperate partitions for /home and /"
date: 2007-08-06
forum: Desktop Environments
---

### Post by sjoseph on 2007-08-06
I have taken some of the lists recs about having a separate partition for / and /home for easy upgrading in the future. One thing i noticed though is that upon start-up, fdsk runs each time and makes start up slower, and shows some discrepancy w the /home partition. It doesn't seem to be a problem, I just wondered if it was normal. Is there a way to stop fdsk from running each time.

---

### Post by mcduck on 2007-08-06
> **sjoseph said:**
> I have taken some of the lists recs about having a separate partition for / and /home for easy upgrading in the future. One thing i noticed though is that upon start-up, fdsk runs each time and makes start up slower, and shows some discrepancy w the /home partition. It doesn't seem to be a problem, I just wondered if it was normal. Is there a way to stop fdsk from running each time.
Could you post here outputs of "cat /etc/fstab" and "sudo fdisk -l"?

---

### Post by sjoseph on 2007-08-06
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0f05e4fd-e750-40ae-bba3-dc8d7b9b53e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=1d4f3cd3-6757-4d45-88b5-d2e4d2980350 /home           ext3    defaults        0       2
# /dev/sda1
UUID=8C4E-3E1E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=EEB76C500064323F /media/sdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=940552e4-73af-4788-aa36-cae4f40fb47e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

AND

---

### Post by sjoseph on 2007-08-06
sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2494    20033023+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1824    14651248+  83  Linux
/dev/sdb2            1825        9729    63496912+   5  Extended
/dev/sdb5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/sdb6            1825        9541    61986739+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
4 heads, 17 sectors/track, 5745911 cylinders
Units = cylinders of 68 * 512 = 34816 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc2   *           2     5745911   195360940    5  Extended
/dev/sdc5               2     5745911   195360931+   7  HPFS/NTFS
sjoseph@sjoseph-desktop:~$

---

### Post by mcduck on 2007-08-07
Try disabling fsck on your windows partitions, that seems to cause problems like you are having. To do this, change the last number from 1 to 0 on thse parition's entries in /etc/fstab. (use 'gksudo gedit /etc/fstab' to open the file for editing).
```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0f05e4fd-e750-40ae-bba3-dc8d7b9b53e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb6
UUID=1d4f3cd3-6757-4d45-88b5-d2e4d2980350 /home           ext3    defaults        0       2
# /dev/sda1
UUID=8C4E-3E1E  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdc5
UUID=EEB76C500064323F /media/sdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sdb5
UUID=940552e4-73af-4788-aa36-cae4f40fb47e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

After that reboot and hopefully everything works now fine. :)

---

### Post by sjoseph on 2007-08-07
thanks, i'll give it a try.

---

### Post by sjoseph on 2007-08-07
thanks, it worked like a charm..all the best.. steve

---

