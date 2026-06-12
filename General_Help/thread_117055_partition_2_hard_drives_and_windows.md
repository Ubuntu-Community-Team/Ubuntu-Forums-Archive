---
title: "partition 2 hard drives and windows"
date: 2006-01-14
forum: General Help
---

### Post by Randar on 2006-01-14
I'm trying to install Ubuntu to a machine with two hard drives. master is 80gb (with windows using 50gb of it) and slave is 100gb. I'm wanting to put Ubuntu on the other 30gb of the master and use the slave for extra spaceon Ubuntu.

I did a manual partition and made the 100gb "/ron" but it only mounts read only. It also shows "/ron" as only 2gb.
The devices tab in system monitor shows "hdc3    /    ext3   4.6gib" "hdc4   /home   ext3   20.7gib" "hdc1    /media/hdc1   ntfs   48.8gib" with no sign of the 100gb hard drive.

I'm willing to do a fresh install if it is the best way to go.

Here is what my fstab said. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc4       /home           ext3    defaults        0       2
/dev/hdc1       /media/hdc1     ntfs    defaults        0       0
/dev/hdd5       /ron            ext3    defaults        0       2
/dev/hdc2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by BathroomNinja on 2006-01-14
go to SYSTEM > ADMINISTRATION > DISKS
enter your password if needed

what do you see on the left hand side?

you can click on your 100GB drive here and then 'partitions' to create new partitions and also to choose mount points.


EDIT- sorry, I just woke up.  Also, after you make sure your partitions are setup correctly, your line in /etc/fstab should look something more like this:

/dev/hdd5    /ron    ext3    rw,defaults      0      0




Double EDIT-  I forgot to ask, is the 100GB drive a blank drive?  Nothing installed on it?

---

