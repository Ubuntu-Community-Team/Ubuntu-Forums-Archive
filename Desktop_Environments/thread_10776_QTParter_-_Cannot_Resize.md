---
title: "QTParter - Cannot Resize"
date: 2005-01-11
forum: Desktop Environments
---

### Post by deception on 2005-01-11
I've installed and run QTParted. I want to resize my ext3 partition, to give Windows more space so I can restore a backup image onto it. 

On QTParted, Resize is greyed out on both the NTFS partition and the ext3 partition, any ideas why?

Many thanks
Matt

---

### Post by Johan on 2005-01-11
Are the partitions mounted? In that case try unmounting them first.

---

### Post by deception on 2005-01-11
Thanks very much for the response. 

How do I unmount the NTFS partition?  :confused:

---

### Post by az on 2005-01-11
You will have trouble unmounting your partition while you are running from it.  Use the ubuntu boot cd to resize your ext3 partition.

Boot from it and make your way to the partitionner.  Select your ext3 partition and make change the size to a smaller size.  Make it go and then reboot.

The problem you will find is that to resize a partition, the starting point must stay fixed.  So, if your ext3 partition is after your windows partition, you will resize from the end and not from the beginning.  You will end up with free space after your ext3 partition.

If you have enough space, you can create enough free space at the end of your disk to then move the shrunk ext3 partitoin there (copy).

If you find that complicated, you can just create a fat32 partition after your ext3 partition and use that for storage for your windows.  The problem with moving your linux partition around is that the partition name is changed and you must modify your /etc/fstab before you boot from it.  Again, this can be done from the ubuntu boot cd, but you will have to use the minimal tools provided by the shell prompt (ctrl-F2)

Good luck!

BTW: You can boot a knoppix cd and use qtparted to move things around easily.  You can then modufy the fstab too.

---

### Post by deception on 2005-01-11
Thank you for the comprehensive reply! 

In the end I deleted all partitions and installed XPPro, imported the backup image, and installed Ubuntu on a new partition. 

Many thanks
Matt

---

