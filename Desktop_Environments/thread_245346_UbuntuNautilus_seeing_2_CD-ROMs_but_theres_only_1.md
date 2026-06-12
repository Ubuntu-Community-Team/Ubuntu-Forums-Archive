---
title: "Ubuntu/Nautilus seeing 2 CD-ROMs but theres only 1"
date: 2006-08-27
forum: Desktop Environments
---

### Post by glycerin on 2006-08-27
Not sure why this is happening but when I go to the address "computer:///" in nautilus I am seeing 2 CD-ROMs - even though there is actually only one connected to the system. It only showed one when Ubuntu was first installed but now something has changed and I don't know what. Here's a pic:

[IMG]http://img167.imageshack.us/img167/3932/2cdromsah8.png[/IMG]

Here's my fstab incase that may have anything to do with this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>		<options>			<dump>  <pass>
proc            /proc           proc		defaults			0       0
/dev/hde1	/media/hde1	ntfs-fuse	auto,gid=1002,umask=0007	0	0
/dev/sda2       /               ext3		defaults,errors=remount-ro	0       1
/dev/sda1       none            swap		sw				0       0
/dev/hdb        /media/cdrom0   		udf,iso9660 user,noauto		0       0

```
Here's my /media folder:
```
total 8
lrwxrwxrwx 1 root root    6 2006-07-09 05:19 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-07-09 05:19 cdrom0
drwxrwx--- 1 root ntfs 4096 2006-08-08 00:17 hde1
```

---

### Post by glycerin on 2006-08-27
Here's some more pictures. Here's what I get if I double click on "CD-ROM 1" in nautilus:
[IMG]http://img244.imageshack.us/img244/5442/errorfx2.png[/IMG]

Here's what I get if I try to delete "CD-ROM 1" while in nautilus with gksudo:
[IMG]http://img90.imageshack.us/img90/8866/notpermittednp4.png[/IMG]

This may have happened because the CD-ROM used to be /dev/hdb but it is now /dev/hda because there was a drive removed making it now a master instead of slave on the IDE.

---

### Post by glycerin on 2006-09-23
Still waiting for any help. If you have any suggestions please toss them out.

---

