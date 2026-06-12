---
title: "Replace disk with / and /home and /swap on it"
date: 2009-06-10
forum: General Help
---

### Post by sylaan on 2009-06-10
Hi all, 

I have 3 disks in my Ubuntu 9.04 server and one of them is failing. It's still working but I started hearing the clicks of death so its days are numbered. 

This is the primary disk and /, /home and a swap partition are on it. I have this server ever since Ubuntu 7 and I would want to avoid reinstalling everything. Currently fdisk shows this:

```
root@neriak:/var/log# fdisk -l /dev/sda

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a53e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         262     2104483+  82  Linux swap / Solaris
/dev/sda2   *         263        2873    20972857+  83  Linux
/dev/sda3            2874        4179    10490445   83  Linux
/dev/sda4            4180       30401   210628215   8e  Linux LVM
root@neriak:/var/log# mount | grep sda
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda3 on /home type ext3 (rw,relatime)
```

What would be the easiest way of replacing this ? I imagine dd would be a good idea. I plan to replace it with a much smaller disk though, smaller than the current 250GB since I don't need that size anymore. Would that cause problems with dd ?

Thanks in advance. 

Regards,
Sylaan

---

### Post by Legace on 2009-06-10
Use tar, not dd, because tar only copies files (while dd also copies empty space, which will make it messy to restore to a smaller disk).
-> [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

