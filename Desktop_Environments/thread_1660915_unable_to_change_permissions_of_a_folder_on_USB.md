---
title: "unable to change permissions of a folder on USB"
date: 2011-01-06
forum: Desktop Environments
---

### Post by jamesbon on 2011-01-06
I am having a USB disk.
I want to change the permissions of  folder on it from 700 to 755 (and all subdirectories in it)
ls -l shows

total 26
> drwxrwxrwx 2 bond bond  2048 2010-02-12 04:12 HPLAUNCHER
drwx------ 7 bond bond  4096 1970-01-01 05:30 vol1
drwx------ 1 bond bond 20480 2011-01-03 17:43 vol2



how ever even if I am trying it as root this is not happening.

>  chmod -R 755 /media/vol2

This is the command I try always and after the cursor blinks for about 5-6 minutes I get the shell back.
What could be the problem?

Some outputs I am posting 
lsusb shows
> Bus 002 Device 002: ID 03f0:4507 Hewlett-Packard 

fdisk -l shows
> Disk /dev/sdb: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x579a78f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       59918   481283302+   f  W95 Ext'd (LBA)
/dev/sdb2           59919       60715     6401902+   c  W95 FAT32 (LBA)
/dev/sdb5               2       59918   481283271    7  HPFS/NTFS


-- 

Output from /var/log/syslog  is
> 
Jan  6 10:24:12 bond ntfs-3g[2278]: Version 2010.3.6 external FUSE 28
Jan  6 10:24:12 bond ntfs-3g[2278]: Mounted /dev/sdb5 (Read-Write, label "vol2", NTFS 3.1)
Jan  6 10:24:12 bond ntfs-3g[2278]: Cmdline options: rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077
Jan  6 10:24:12 bond ntfs-3g[2278]: Mount options: rw,nosuid,nodev,uhelper=udisks,silent,allow_other,nonempty,relatime,fsname=/dev/sdb5,blkdev,blksize=4096,default_permissions
Jan  6 10:24:12 bond ntfs-3g[2278]: Global ownership and permissions enforced, configuration type 1

---

### Post by tad1073 on 2011-01-06
you need to "sudo" the chmod command.

```
sudo chmod -R 755 /media/vol2
```

---

### Post by jamesbon on 2011-01-06
> **tad1073 said:**
> you need to "sudo" the chmod command.

```
sudo chmod -R 755 /media/vol2
```
Did you read my post? Excerpts from my post above 
> **jamesbon said:**
> 
 how ever even if I am trying it as **root** this is not happening.
 

---

### Post by mcduck on 2011-01-06
FAT and NTFS are Windows filesystems, and lack support for ownerships and permissions as Linux/Unix systems use them. You can't chown or chmod on those filesystems, they simply have no way to handle such thing.

Instead the permissions are set for the whole partition at the time it's mounted.

---

