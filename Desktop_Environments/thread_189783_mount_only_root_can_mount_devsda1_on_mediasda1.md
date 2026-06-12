---
title: "mount: only root can mount /dev/sda1 on /media/sda1"
date: 2006-06-05
forum: Desktop Environments
---

### Post by eeclark on 2006-06-05
Why do I get "mount: only root can mount /dev/sda1 on /media/sda1

" when inserting a USB key drive?

---

### Post by eeclark on 2006-06-05
Resolved:
I commented out the /dev/sda1 entry in my fstab.

Now when I insert the USB key drive, it appears and opens on my desktop.
When I installed 6.06, my USB key was inserted so I guess it wrote it right into the fstab during its creation.

my fstab:
```

edward@smallville:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       /home           ext3    defaults        0       2
#/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hda1       /windows        vfat    defaults,utf8,umask=007,gid=46 0       0/dev/hdc5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
edward@smallville:/etc$


```

---

### Post by geog_eric on 2006-06-05
Thanks! This worked for me, too. I also had the USB drive connected during install and an fstab entry was automatically added.

---

### Post by eeclark on 2006-06-05
Glad I could help. :-)

---

### Post by Teunis on 2006-06-07
I was having the same problem, same reason :)
But one addition, taking the line out of fstab did not work for me, when inserting the USB device it would be recreated with the same root only message.
Only when I deleted the /dev/sda1 line from fstab WHILE the device was connected the problem did not return.

---

### Post by cenora on 2006-07-26
The /etc/fstab hack worked for me as well, but it's quite amazing to me that ubuntu (the great "for everybody" linux) has not made the hotswap default. ](*,)

---

