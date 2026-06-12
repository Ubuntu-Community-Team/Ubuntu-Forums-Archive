---
title: "Messed up /etc/fstab"
date: 2006-06-01
forum: Desktop Environments
---

### Post by jet87 on 2006-06-01
Hello all.  I tried to follow the directions for using fuse for read/write support of a NTFS partition, but it failed to work.  From the thread, I thought things would Just Work so I didn't backup my /etc/fstab ](*,) .  Could someone tell me how to fix fstab so that I can use my NTFS drive without superuser powers?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1    	/media/hda1    ntfs    auto,gid=1001,umask=0002    0    0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by aysiu on 2006-06-01
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jet87 on 2006-06-01
Thanks!  Now I just need to remember to make backups before I mess around with important files.  Hopefully I'll be able to get ntfs-fuse working soon;  for some reason it appeared that Ubuntu didn't recognize it as a valid partition type.

---

