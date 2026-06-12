---
title: "Moving /home"
date: 2006-01-03
forum: Desktop Environments
---

### Post by agds on 2006-01-03
I know similar questions have been asked before, but I didn't find an answer specific to my situation on the forums.  (Of course, if I've missed a relevant thread, please inform me.)

I have a dual-boot system with Ubuntu as the default and XP for gaming and such.  When I installed Ubuntu on this machine, I was new to Linux.  It never occurred to me that I ought to put /home on a separate partition.  Now I'd like to correct my mistake, but naturally I want to make sure all my data survives the transition.

Here's my current /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/hdb1     vfat    user,umask=000  0       0
```
The second HDD, mounted at /media/hdb1, is where I keep all my data.  That's the partition where I'd like /home to be.  So…what do I need to do?  Sorry, I'm a complete ignoramus about this sort of thing.

---

### Post by HermanAB on 2006-01-03
OK, you need to do something like the following - hard to be exactly right without actually doing it:
a. quit X (init 3 or some such)
b. copy /home to /media/hdb1 keeping all attributes intact (copy -a /home /media/hdb1)
c. delete the contents of the present /home (rm -Rf /home/*)
d. unmount /media/hdb1 (umount /media/hdb1)
e. mount hdb1 on /home (mount -t vfat /dev/hdb1 /home)
f. modify /etc/fstab to suit

Hope that helps!

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

