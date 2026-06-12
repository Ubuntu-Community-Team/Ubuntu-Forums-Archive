---
title: "Startup error HELP!"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-28
Hi When I start my computer I get this thing that says an error on your filesystem has occoured please repair manually

can anyone help here please?

here is my /etc/fstab file

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1

/dev/hdb1 /foo ext3 defaults,errors=remount-ro 0 2


/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

/dev/hdb1 /media/hdb1 ext3 nodev,nosuid 0 2
Edit/Delete Message

---

### Post by pseudonym on 2006-09-29
Did you follow [this advice]("http://www.ubuntuforums.org/showthread.php?t=265979") that I provided the other day?

A filesystem check needs to be run on a unmounted partition, hence the live cd. Your /etc/fstab shows you are using ext3 as your filesystem, and your / partition is /dev/hda1. Your check command should be - ```
sudo fsck.ext3 /dev/hda1
``` If errors are found, you need to re-run the check with repair options - ```
sudo fsck.ext3 -pvf /dev/hda1
``` It will then go to work making your filesystem consistent again.

One other thing - why does /dev/hdb1 have 2 mountpoints in your fstab? You should remove this line from it - ```
/dev/hdb1 /foo ext3 defaults,errors=remount-ro 0 2
``` 

See how you go with this and report back.

---

