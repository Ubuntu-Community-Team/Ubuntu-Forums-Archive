---
title: "resizing ext3 partition"
date: 2006-07-01
forum: Desktop Environments
---

### Post by sveinn on 2006-07-01
Hello, 

I dual boot XP/6.06, and I just shrunk the NTFS partition and had intended to expand the ext3 into the empty space, but GParted and Qtparted won't let me.

Here's the current partition setup:

/dev/sda1   fat16
/def/sda2    ntfs
unallocated
/def/sda4    extended
  /def/sda5  ext3
  /def/sda6  linux-swap
/def/sda3    fat32

Any suggestions on how to resize the extended/ext3 partition to take advantage of the unallocated space?

I've tried booting  Ubuntu CD and running GParted but it makes no difference, it won't let me expand ext3, only decrease it.  

This issue has also  been discussed here:

[http://ubuntuforums.org/showthread.php?t=195357](http://ubuntuforums.org/showthread.php?t=195357)

but there is no fix posted. 

Thanks, 

Sveinn

---

### Post by ajgreeny on 2006-07-01
The problem is that you can't move the starting point of your ext3 partition back towards the beginning of the drive.
You will need to use *partimage* or similar, to make a backup of the whole ubuntu partition to another,perhaps temporary, partition or another drive, then delete the whole ubuntu partition.  Now you can use all the free space, including the bit you have freed from windows, and make a completely new partition formatted to ext3.  Now restore the partition from partimage into the new ext3 and you should be back where you were, but with a larger ubuntu partition.  You can restore a partimage image to a larger sized partition, but not a smaller one; if you try that you will end up with errors or just not being able to restore at all.  Best of luck!

---

### Post by RRS on 2006-07-01
In [this thread]("http://www.ubuntuforums.org/showthread.php?p=1143498#post1143498") Herman explains how to use copy/past in gparted to move partitions so they can be resized and also to put Ubuntu on the first partition of the disc instead of windows.

I've tried the procedure and it works, though a proper study(take notes) and proper planning befoe hand helps. 

I did it from memory and it took a while to get it right so the disk labels remained original to prevent grub errors.

---

