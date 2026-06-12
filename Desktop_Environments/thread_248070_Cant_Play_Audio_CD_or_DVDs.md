---
title: "Cant Play Audio CD or DVDs"
date: 2006-08-31
forum: Desktop Environments
---

### Post by opticyclic on 2006-08-31
I am running Dapper with KDE.
When I insert an Audio CD (or a DVD) it appears as an icon on the desktop.
When I right click and select play I get
```
CD-ROM read or access error (or no audio disc in derive)
Please make sure you have access permissions to:
/dev/hdc 
```
No matter which player I try, I cant seem to play my CDs or DVDs. :(

Output of mount
```
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
```
Contents of /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by opticyclic on 2006-08-31
A bit more information:
Its a Dell Latitude D600
The Audio CDs work fine in Windows XP as do the DVDs when using VLC

---

### Post by opticyclic on 2006-08-31
Turns out to just be users and groups permission issue!
It works as soon as I add myself to all these groups!
[http://www.ubuntuforums.org/showthread.php?t=233509](http://www.ubuntuforums.org/showthread.php?t=233509)

---

