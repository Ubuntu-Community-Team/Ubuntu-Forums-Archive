---
title: "How to mount an external Usb drive"
date: 2006-08-09
forum: Desktop Environments
---

### Post by kpolice on 2006-08-09
Here is my problem: I got a new external USB drive and I created 5 partitions 
- NTFS
- FAT32
- FAT32
- FAT32
- EXT3

When I plug in the disk every partition is mounted, I can read and write to the FAT32 partitions, read the NTFS partition and read the EXT3 partition.

I want to read/write the EXT3 but if I try to create a file on it all I get is that i don't have permission to do it and the only way is to use sudo. Is there a way to do it without sudo-ing?? 

My fdisk output is:
```
Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       28244   226869898+   7  HPFS/NTFS
/dev/sdc2           28245       48641   163838902+   f  W95 Ext'd (LBA)
/dev/sdc5           28245       32451    33792696    b  W95 FAT32
/dev/sdc6           32452       40610    65537136    b  W95 FAT32
/dev/sdc7           40611       44817    33792696    b  W95 FAT32
/dev/sdc8           44818       48641    30716248+  83  Linux

```

---

### Post by SenseiJonny on 2006-08-16
kpolice, I just started playing around with Ubuntu, but it sounds like you are just having a permissions problem on the ext3 partition.  To fix it so that you do not need to use sudo, use the "chmod" command to change the permissions.  For example:

```

sudo chmod 0777 <mount point of partition>
```

Find where the mount point is (probably /media/sdc8 ) and insert that into the above code.  That code will give read, write, and execute permissions to the user that owns the directory/files, group, and other users.  If you want different permissions, check out how to use chmod or just post another question.

---

