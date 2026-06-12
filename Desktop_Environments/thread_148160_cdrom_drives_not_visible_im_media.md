---
title: "cdrom drives not visible im /media:/"
date: 2006-03-21
forum: Desktop Environments
---

### Post by anjilslaire on 2006-03-21
I cannot locate my cdrom discs in (K)ubuntu. If I load up k3b, I can rip the contents/copy/etc, but when I put in a cd (audio/data/whatever) it doesn't show up anywhere. Isn't it supposed to automount and be accesible? I'm at a loss. Any thoughts?
Here is my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
/dev/hdb1 /windows ntfs nls=utf8,umask=0222,uid=0,gid=0,auto,rw,nouser 0 0
#/dev/sdb1    /media/lexar128   vfat   iocharset=utf8,umask=0000   0   0


```

---

### Post by GoldBuggie on 2006-03-22
do a ```
sudo adduser hal disk
``` then reboot and media:/ should behave correctly.

---

### Post by anjilslaire on 2006-03-22
Thank you!

Edit:
Fixed the rest of my media problems here:
[http://ubuntuforums.org/showthread.php?t=81836&page=2](http://ubuntuforums.org/showthread.php?t=81836&page=2)

---

