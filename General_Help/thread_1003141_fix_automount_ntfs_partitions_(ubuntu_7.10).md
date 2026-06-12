---
title: "fix automount ntfs partitions (ubuntu 7.10)"
date: 2008-12-05
forum: General Help
---

### Post by yilin on 2008-12-05
My ubuntu 7.10 automatically mount all my windows (ntfs) partitions originally. But after I resized windows partition and exchanged the driver letters, one of the ntfs partition is not automounted.

Anywhere I can fix the setting? Thanks a lot.

The partition (Workspace) should mount to /media/sda7, but if I manually mount it, it'll mount to /media/Workspace instead of /media/sda7, (the folder  /media/Workspace is created on the fly).read only.

---

### Post by ajmorris on 2008-12-06
hi there,
you can change all these partition mounting options in the file; /etc/fstab   so just edit it as root, and edit the physical block devices for your partition, and mount points, as you see fit.

You can check your partitions with  ```
sudo fdisk -l
```


Also, im not sure what you mean when you say:
> The partition (Workspace) should mount to /media/sda7, but if I manually mount it, it'll mount to /media/Workspace instead of /media/sda7, (the folder /media/Workspace is created on the fly).read only.

If you manually mount a partition, you usually specify the mount point also, if no mountpoint is specified, it will use whatever is specified in /etc/fstab for that partition. Also, the reason why it would have been read only, is because in the ubuntu kernel, the ntfs kernel module is compiled without write support. To write to an ntfs partition, you must use the ntfs-3g tool. So if you mount the partition manually, you must specify the  
-t ntfs-3g  mount paramater.


AJ

---

### Post by kpkeerthi on 2008-12-06
You might want to change the device names in the file [/etc/fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by yilin on 2008-12-06
Dear All. Thanks so much for your replies. It's really encouraging for a starter.

Here is my list -l result for /media. Notice the last line got a 2 before root. I doubt this could be a problem. Since the line with sda4 got the same 2 and it's a hidden partition for windows backup. Which also not auto mounted.
 
total 32
lrwxrwxrwx 1 root root       6 2008-11-28 03:51 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2008-11-28 03:51 cdrom0
lrwxrwxrwx 1 root root       7 2008-11-28 03:51 floppy -> floppy0
drwxr-xr-x 2 root root    4096 2008-11-28 03:51 floppy0
-rw-r--r-- 1 root root       0 2008-12-06 13:48 media_list-l.txt
drwxrwx--- 1 root plugdev 8192 2008-12-06 13:37 sda1
drwxr-xr-x 2 root root    4096 2008-11-28 03:51 sda4
drwxrwx--- 1 root plugdev 4096 2008-12-06 13:37 sda5
drwxrwx--- 1 root plugdev 4096 2008-12-06 13:37 sda6
drwxrwx--- 2 root plugdev 4096 2008-11-28 03:51 sda7
=======================================
Here is my sudo fdisk -l result:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xfc8afc8a

   Device Boot   Start    End   Blocks  Id System
/dev/sda1   *        1    679  5133208+  7 HPFS/NTFS
/dev/sda2          680   8388 58280040   f W95 Ext'd (LBA)
/dev/sda3         8389   9693  9865800  83 Linux
/dev/sda4         9694  10337  4868640  1c Hidden W95 FAT32 (LBA)
/dev/sda5          680   1898  9215608+  7 HPFS/NTFS
/dev/sda6         1899   3222 10009408+  7 HPFS/NTFS
/dev/sda7         3223   5714 18839488+  7 HPFS/NTFS
/dev/sda8         5715   8263 19270408+ 83 Linux
/dev/sda9         8264   8388   944968+ 82 Linux swap / Solaris
================================================================
Here is the content of etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a8c1d46c-6407-4d55-bdc9-e5f47a31ab5f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda8
UUID=c17b6d4c-9531-4111-894b-679163c81384 /home           ext3    defaults        0       2
# /dev/sda1
UUID=106CD43C6CD41DF2 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=4759-1659  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=14EBABACADEE5A41 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=53AEB0B79199EE04 /media/sda6     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=BC491926A0F71009 /media/sda7     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=6b1e2fe2-cdf3-46af-ae08-b47a38f1f3af none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

==============================================================
This is why I'd say the partition should(supposed) got mount point /media/sda7 instead of /media/Workspace where "workspace" is the partition label from Windows.

Sorry I confused you about "manual mount". What I meant is that from "Places" I lauched "File Browser" for Computer and then I saw the disk icon called "Workspace", and I right click it and choose "Mount Volume" option.

It is interesting that when I compare the properties of the ntfs partitions of a working one the the problematic one, I got quite different thing:

working one:
Owner: root    Folder Access: create and delete files (grayed)
Group: plugdev Folder Access: Create and Delete files (grayed)
Others:        Folder Access: None (Grayed)
Mount Point: /media/sda6
File System: fuseblk
Mount Options: rw nosuid nodev user_id=0 group_id=0 default_permissions allow_other

Problematic one:
Owner: unknown     Access: Read-only (not grayed)
Group: unknown     Access: Read-only (not grayed)
Others:            Access: Read-only (not grayed)
Mount Point:       Not Mounted
File System:       Not Mounted
Mount Options:     Not Mounted

My question is, how those info be generated. 

Anyway, that's all I know about. Thanks again in advance for any hints.

---

