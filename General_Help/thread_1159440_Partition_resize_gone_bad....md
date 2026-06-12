---
title: "Partition resize gone bad..."
date: 2009-05-14
forum: General Help
---

### Post by [gato] on 2009-05-14
Hi everyone

I have a 750Gb external hard drive with 2 partitions and wanted to resize them. for that used the "partition editor"

Everithing was good, the firs partition was resized (to a small size) and then the second one was being resized to fill all the left space.

Then my laptop crashed....

Boot up again and when I plug the external drive only the firs partition is mounted the other is not shown.

The "Partition Editor" shows
```
Partition    File System  Label  Size        Used       Unused     Flags
/dev/sdb1    fat32        PS2    150.00 GiB  74.32 GiB  75.68 GiB
/dev/sdb2    unknown             382.58 GiB
unallocated  unallocated         168.79 GiB
```

The second partition should be NTFS and use all the unallocated space.

The extreme solution is erase the /dev/sdb2 and create a new one, but i have data there and I want make all to preserve that.

Using command: sudo fdisk -l /dev/sdb returns this

```
Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bce2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19581   157284351    6  FAT16
/dev/sdb2           19582       69559   401448285    7  HPFS/NTFS

```
Can someone give me some help?

---

### Post by hexanol on 2009-05-14
You say there was a partition right after your second primary partition (i.e. /dev/sdb2) ? One automated tool who can do partition recovery is [TestDisk]("http://en.wikipedia.org/wiki/Testdisk"). Give it a look, there's good chance it will be able to fix your problem.

There's also the manual way, but no, i'm not doing this again, and I think TestDisk will be just fine.

---

