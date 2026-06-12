---
title: "mounting hard drives???"
date: 2009-02-11
forum: General Help
---

### Post by dreken105 on 2009-02-11
hi, i just switched over to xubuntu from ubuntu because i am running on an older computer. ubuntu just lagged too much when i needed to run multiple programs or more intense ones. but it seems xubuntu does not recognize my internal hard drives, i have two additional ones. on ubuntu these were automatically detected and displayed. from what i understand "sudo fdisk -l" would display all connected drives and it seems to detect my HDDs. how can i mount these HDDs with this information?
here is the fdisk -l output:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd31fd31f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1567    12586896    c  W95 FAT32 (LBA)
/dev/sda2            1568        9964    67448902+   f  W95 Ext'd (LBA)
/dev/sda5            1568        9964    67448871    b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec23040

---

### Post by logos34 on 2009-02-11
yes, fdisk should show all connected disks.  If you want to mount sda1 and sda5, read [this]("https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions").

sdb isn't showing partition.  Did you format it?

Where's linux?  Are all the disks being recognized in the Bios?

---

