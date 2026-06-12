---
title: "My 2nd HD unmounted out of nowhere and my desktop bg is gone"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Epperly on 2006-08-05
Can someone help me? I don't remember doing anything for this to happen, I get on windows for a little while to photoshop and burn ISOs and come back onto Ubuntu and my primary (Windows) HD is unmounted and I can't view it... and my desktop background is changed from the image to just a flat blue, and Idk why..

Can anybody help me please??
Thanks!

---

### Post by philippe_carlo on 2006-08-05
Here's what I guess is what happend. You mounted the windows partition and set a wallpaper that is located on that partition. But windows partitions are not automatically mounted. In order for them to do so you need to add an 'auto' directive to the line with the windows partition in /etc/fstab as follows:

```

/dev/hda1       /media/windows  ntfs    rw,user,auto  0       0

```

---

### Post by Epperly on 2006-08-05
Okay that makes it so I can see it and the size but I can't read/write.
(before this I had it mounted by ntfs-fuse)

this is my backup of what I had:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc2       /windows        ntfs-3g     silent,umask=0,locale=en_US.utf8    0    0
```

---

### Post by Epperly on 2006-08-05
Also my internet keeps goin out so something's wrong with maybe Ubuntu and Idk what it is or how to check....

---

