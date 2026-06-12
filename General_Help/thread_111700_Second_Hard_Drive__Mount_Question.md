---
title: "Second Hard Drive / Mount Question"
date: 2006-01-02
forum: General Help
---

### Post by ptmurphy on 2006-01-02
Being fairly new to Ubuntu and Linux, I have trudged my way through adding a second hard drive and auto-mounting using the /etc/fstab file based on some great past messages on this board.  However, I am not sure I did things quite right...

I added the hard drive which is hdb.  I then created an "extended" partition taking up all the space.  This is where I may have gone astray.

I tried mounting /dev/hdb1 to a directory I created (/disk2, which I changed the owner ship to allow RWX for all users), and could not do it.  So I ended up havning to create a "logical" partition under hdb1, which was automatically called hdb5.

I could then mount /dev/hdb5 to /disk2.  Not sure why I had to do this.  Why can I not just mount /dev/hdb1 to /disk2?

Here is my partition table for /dev/hdb...

Disk /dev/hdb: 40.9 GB, 40982151168 bytes
16 heads, 63 sectors/track, 79408 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       79408    40021600+   5  Extended
/dev/hdb5               1       79401    40017852   83  Linux

And here is my fstab file...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb5	/disk2		ext3	defaults	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks for any clarification you can give me or anything else you see I have done wrong.

Phillip

---

### Post by iramhernandez on 2006-01-02
Extended partitions hold logical partitions only.  This is a PC thing, not a linux thing.  What you probably wanted to do was create a primary partition.  You can have up to four primary partitions on a disk  hdb1, hdb2, hdb3, hdb4.  If you choose to make an extended partition instead, the partition will be hdb5, hdb6, hdb7, etc.  You can have an many logical partitions (i dont remember the exact number) but its more than 32, I'm pretty sure.

--
Iram Hernandez

---

### Post by ptmurphy on 2006-01-03
Thanks.  I re-did the partitioning and made a primary and could mount it fine.  One of the guides I used had me create an extended partition but then failed to mention that you had to create a logical partition after that.

Thanks for the help.

Phillip

---

