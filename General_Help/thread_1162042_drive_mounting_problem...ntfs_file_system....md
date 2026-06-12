---
title: "drive mounting problem...ntfs file system..."
date: 2009-05-17
forum: General Help
---

### Post by muctadir on 2009-05-17
i cant mount drives by double cliking the drives.......
it says that you are not privileged to mount the volume....

i need help.........

---

### Post by DFlame on 2009-05-17
If you have Windows installed on that drive, boot into Windows and run through the normal shutdown procedure.

After that, boot Ubuntu and try mounting it again (solution from this thread: [http://ubuntuforums.org/showthread.php?t=892135](http://ubuntuforums.org/showthread.php?t=892135) )

_

If you don't have windows at all (or the above doesn't work anyway), please open the terminal and post the output of this command:

```
sudo fdisk -l
```

DFlame

---

### Post by muctadir on 2009-05-17
output of that command is===


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28612860

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        4378     9566707+  83  Linux
/dev/sda3            4379       30385   208899175+   f  W95 Ext'd (LBA)
/dev/sda5            4379        4844     3743082   82  Linux swap / Solaris
/dev/sda6            4845        8031    25599546    7  HPFS/NTFS
/dev/sda7            8032       11218    25599546    7  HPFS/NTFS
/dev/sda8           11219       17592    51199123+   7  HPFS/NTFS
/dev/sda9           17593       21799    33792696    7  HPFS/NTFS
/dev/sda10          21800       26006    33792696    7  HPFS/NTFS
/dev/sda11          26007       30384    35166253+   7  HPFS/NTFS

---

