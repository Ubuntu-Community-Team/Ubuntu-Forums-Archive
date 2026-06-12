---
title: "problem with burning CDs"
date: 2005-10-19
forum: Desktop Environments
---

### Post by suoko on 2005-10-19
Hi,

I'm experiencing problems with burning CDs both with nautilus and K3b.
Apparently the can erase CD-RW successfully but then they can't write any datas on them. They just create a multisession with no data.

CD burner is a WAITEC STORM 52x 

this is my fstab.

/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /boot           ext3    defaults        0       2
##/dev/hdb5       /media/hdb5     ext3    defaults        0       2
/dev/hdb5        /home          ext3    defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


please help me.

---

### Post by yage on 2005-10-19
If you could start k3b from a terminal and paste the error you get it would be much easier to help you.. 
My /etc/fstab looks like this and burning is no problem:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           xfs     defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by suoko on 2005-10-20
Actually now k3b works well (although I didn't change any configuration) but I'm still experiencing problems with the nautilus burner.
It apparently erases CD-RW and burn the CDs the CD but the strange thing I noticed is that it's TOO fast in creating the image to be written. On another PC  (which has a similar configuration in terms of CPU, RAM and HD and also have breezy installed) I saw it takes more than one minute to create a 650MB image while on this PC it's a question of seconds.
After burning (which it says it is successfull) the CD results unreadable.

I think something's wrong in the image creation process.

Any hints?


Moreover when I insert a blank CD-R or CD-RW I'm asked if I want to create an audio, a photo or a data CD. If I choose photo or data a new nautilus window opens correctly while if I choose audio nothing happens. Is this a bug or do I need to install an extra package?

---

