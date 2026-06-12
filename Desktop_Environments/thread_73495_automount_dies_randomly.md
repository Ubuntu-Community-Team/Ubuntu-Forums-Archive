---
title: "automount dies randomly"
date: 2005-10-09
forum: Desktop Environments
---

### Post by anatole on 2005-10-09
hi,
my problem is that automounting of cdroms and usb devices acts totally randomly. sometimes it works, sometimes it doesn't, in this case, nothing happens and i have to mount my media stuff manually. my question is: is anyone experiencing the same problem? i absolutely have no understanding in automount, so someone please tell, where should i look for the errors? thanks in advance! :)

---

### Post by chinaski on 2005-10-09
I think you have to check /etc/fstab

```
sudo gedit /etc/fstab
```

maybe post the content of it

---

### Post by anatole on 2005-10-09
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               xfs     defaults        0       1
/dev/hdb1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hde        /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb3    /hdd/fat32    vfat    umask=000    0    1
/dev/hda1    /hdd/win    ntfs    umask=000    0    1
/dev/hdb4    /hdd/store    ext3    defaults    0    1
/dev/hda2    /hdd/store2    ext3    defaults    0    1
/dev/sdc2 /media/IPOD vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

now i just remembered that i added the last line recently when i was setting up my ipod, according to a forum post... i tried commenting the last line, now i'll see what will happen, but this shouldn't have to do anything with cdroms, am i wrong?

---

