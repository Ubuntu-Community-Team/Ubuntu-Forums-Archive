---
title: "Ubuntu Kernel: cdrom: open failed."
date: 2005-01-26
forum: Desktop Environments
---

### Post by Jad on 2005-01-26
Hi, I'm not able to eject my CDRW 

watching the /var/log/messages gave me this, 


```
Jan 26 17:00:06 ubuntu -- MARK --
Jan 26 17:07:47 ubuntu kernel: udf: registering filesystem
Jan 26 17:07:49 ubuntu kernel: cdrom: open failed.
Jan 26 17:07:49 ubuntu kernel: cdrom: open failed.
Jan 26 17:09:00 ubuntu last message repeated 8 times
Jan 26 17:12:54 ubuntu kernel: cdrom: open failed.
Jan 26 17:12:54 ubuntu kernel: cdrom: open failed.
```

and here is my /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```



please advise.

---

### Post by matid on 2005-01-26
Try this:
```
umount -f /dev/hdc
```

---

### Post by Jad on 2005-01-26
jad@ubuntu:/media $ sudo umount -f /dev/hdc
umount2: Invalid argument
umount: /dev/hdc: Illegal seek

---

### Post by grj on 2005-01-26
try this

mount <enter>

This will return everything that is mounted.

If you see cdrom, cdrom0 or something similar try

umount [mount point from above]

example
umount /media/cdrom0

---

### Post by Jad on 2005-01-26
hmm 
weird it doesn't seems to be mounted
jad@ubuntu:/media $ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)

---

### Post by matid on 2005-01-26
Have you tried to eject it after shutdown? (if you cannot do this after shutdown but before system started booting than your cdrom drive is down).

---

### Post by Jad on 2005-01-26
[QUOTE=matid]Have you tried to eject it after shutdown? (if you cannot do this after shutdown but before system started booting than your cdrom drive is down).[/QUOTE]
 when I reboot, and before system loaded, I can eject it
but once the system loaded I cant eject it.

---

### Post by jdong on 2005-01-26
So are you using the default Ubuntu kernel? The 2.6.9 series are PLAGUED with these issues.


Can you eject as root?

---

### Post by Jad on 2005-01-26
[QUOTE=jdong]So are you using the default Ubuntu kernel? The 2.6.9 series are PLAGUED with these issues.


Can you eject as root?[/QUOTE]
 root@ubuntu:/home/jad/Desktop/NLD2Ubuntu/ZendStudio-3_5_2 # uname -a
Linux ubuntu 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

dunno whats going on, it was working just fine, all of that happened after installing K3B
is it the  QT Smell? :D

---

### Post by woland on 2005-12-25
I had this error 2 times, one a few month ago and one now. I found the solution for the first time, but can't find it now when I need it.
There is a legacy mounting system that I can't remeber its name. You need to use it to umount it.

---

