---
title: "Fails to change permission for folders/files on vfat partition"
date: 2005-06-19
forum: Desktop Environments
---

### Post by Nils-Johan on 2005-06-19
Hello,
I can't change the permissions on my vfat partition. I created it as root and now i want that any user should be able to read *and* write as we share our photos there...
This was my first fstab;
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /boot           ext2    defaults,noatime      0       2
/dev/hda4       /               ext3    defaults        0       1
/dev/hda2       none            swap    sw              0       0
/dev/hda1       /osshare        vfat    defaults        0       0
/dev/hdc        /media/cdrom0   auto    rw,users,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,users,noauto  0       0 

My current fstab;
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /boot           ext2    defaults,noatime      0       2
/dev/hda4       /               ext3    defaults        0       1
/dev/hda2       none            swap    sw              0       0
/dev/hda1       /osshare        vfat    rw,users,exec,auto,async,suid        0       0
/dev/hdc        /media/cdrom0   auto    rw,users,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,users,noauto  0       0

What am i doing wrong?  ](*,)

---

### Post by TripHammer on 2005-06-19
Try:

/dev/hda1 /osshare vfat rw,users,exec,auto,async,umask=0000

umask works like the inverse of 'normal' file permissions: umask 0000 = 777, umask 0022 = 755 etc.

---

### Post by Nils-Johan on 2005-06-19
Thanks for the fast reply.

should i then use the unmask variable with the userid?

---

### Post by Nils-Johan on 2005-06-19
never mind the last post....

---

