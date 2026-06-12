---
title: "fstab issues, trying to mount 2nd hard disk"
date: 2006-08-31
forum: Desktop Environments
---

### Post by fig_jam_uk on 2006-08-31
Hey peeps, just hoping someone can help... Im trying to mount my 2nd hdd wich is sdb1 it is formatted as ext3 and whatever I try I cant get it to mount.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1	/hdd/1		ext3	umask=0222 0 0
/dev/hda1       /hdd/2		ntfs    user,umask=0222      0       0

```

If i try to mount it mannuall I get:

```
mark@mark-desktop:~$ sudo mount /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and using the disks manager I get it tells me that its not available. If anyone out there can help I would realy appreciate it... :?: :?: :?: :?:

---

### Post by xyz on 2006-08-31
Try that one:
[http://www.ubuntuforums.org/showthread.php?t=119209](http://www.ubuntuforums.org/showthread.php?t=119209)

---

### Post by aysiu on 2006-08-31
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by fig_jam_uk on 2006-08-31
Cheers for the responce folks, ill have a look and see if I can get it to work, Hopefully its not the hdd dying as its only 2 weeks old and ill have to send it back to microdirect and wait till a replacement is sent :sad: but hopefully its just a case of changing the fstab to accomodate it...

---

### Post by fig_jam_uk on 2006-09-01
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

Work great, thanks

---

