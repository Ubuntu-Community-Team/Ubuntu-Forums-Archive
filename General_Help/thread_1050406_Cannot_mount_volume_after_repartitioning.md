---
title: "Cannot mount volume after repartitioning"
date: 2009-01-25
forum: General Help
---

### Post by nr4ps on 2009-01-25
I have a Western Digital My Passport external hard drive.  I used GParted to shrink the FAT32 partition and make an ext3 partition in the freed space.  The ext3 partition is working fine, but now I can't mount the FAT partition.

Results of sudo fdisk -l:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          15      120456   de  Dell Utility
/dev/sda2   *          16       16588   133122622+   7  HPFS/NTFS
/dev/sda4           16589       19457    23045242+   5  Extended
/dev/sda5           18922       19457     4305388+  82  Linux swap / Solaris
/dev/sda6           16589       18921    18739759+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26227   210668346    c  W95 FAT32 (LBA)
/dev/sdb2           26228       38913   101900295   83  Linux

```

Results of dosfsck /dev/sdb1:
```

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!

```

When I connect the drive, it tells me "Cannot mount volume.  Unable to mount the volume 'My Passport'."  Details: "mount: /dev/sdb1: can't read superblock"

I can still see all the file names in testdisk.  Is there any way to fix the mounting problem?  Or at least recover the files?

Thanks.

---

### Post by taurus on 2009-01-25
Why don't you boot up windows (from /dev/sda2) and run a scandisk of that fat32 partition?

---

### Post by nr4ps on 2009-01-25
When I try to browse the drive in Windows:

```

G:/ is not accessible.

The file or directory is corrupted and unreadable.

```


And chkdsk in Windows:

```

(snip)
\Lectures\ENAE483_F08\2008-09-04\SupportingFiles\Popups  first allocation unit i
s not valid. The entry will be truncated.
\Lectures\ENAE483_F08\2008-09-04\SupportingFiles\Scripts  first allocation unit
is not valid. The entry will be truncated.
\Lectures\ENAE483_F08\2008-09-04\SupportingFiles\speakers  first allocation unit
 is not valid. The entry will be truncated.
\Lectures\ENAE483_F08\2008-09-04\SupportingFiles\Themes  first allocation unit i
s not valid. The entry will be truncated.
File and folder verification is complete.
Convert lost chains to files (Y/N)? y
Insufficient disk space to recover lost data.
43736000 KB in 16449 recoverable files.
Windows found problems with the file system that could not be corrected.
  210,616,864 KB total disk space.
           32 KB in 1 hidden files.
       50,048 KB in 1,550 folders.
   27,028,384 KB in 28,423 files.
  139,802,048 KB are available.

       32,768 bytes in each allocation unit.
    6,581,777 total allocation units on disk.
    4,368,814 allocation units available on disk.

```

Any thoughts?

---

### Post by nr4ps on 2009-01-25
Ah, it seems that while chkdsk was not able to recover all the files, it was able to fix whatever was making the drive unreadable.  So I got some of my files back.  That'll work, I suppose.  Most of the files on there were just backups anyway.  I think I'll use this excuse to reformat in NTFS rather than FAT.  Thanks for your help.

---

