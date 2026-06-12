---
title: "partition issue!! HELP!!!"
date: 2006-12-07
forum: Desktop Environments
---

### Post by rkakkar on 2006-12-07
i have an 80gb hdd which has been partitioned as follows

ext3 - 3GB - ubuntu
swap - 1GB 
fat32 - 70GB

however none of my apps can by default save onto my fat32 partition. if i manually copy, it works. but if i try to download something through firefox or save a file through gedit i keep getting an "operation not permitted" error. my fstab looks like follows:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=027da045-bc1d-4f0f-914b-024e58c0c947 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3950-3643  /media/data     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=6ea753e0-eb75-47c8-92ef-5fbb5e1df016 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by taurus on 2006-12-07
I would change the entry for /etc/hda5 to look like this.

```

UUID=3950-3643  /media/data     vfat    iocharset=utf8,umask=000   0   0 

```
Reboot and see if you can write to /media/data.

---

### Post by rkakkar on 2006-12-07
no no you don't get me.. i am able to save but only if i do it manually (for eg cp). however if some application tries to save.. it gives me this error. for instance .. i was using wget.. and this is what i got:

```

Length: 781,565 (763K), 331,237 (323K) remaining [application/x-java-archive]

100%[+++++++++++++++++++++++++++++++++++++++++++++++==================================>] 781,565        8.24K/s    ETA 00:00

utime(ifox_graphite-2.4.1-fx.jar): Operation not permitted
22:13:50 (2.54 KB/s) - `ifox_graphite-2.4.1-fx.jar' saved [781565/781565]

```

here its giving me an "operation not permitted" error but at the same time it also saved the file :confused: 

i tried again with another file.. same error:

```

Length: 205,284 (200K) [text/plain]

100%[=================================================================================>] 205,284        1.98K/s    ETA 00:00

utime(automatix2_1.1-2.2-6.10edgy_i386.deb): Operation not permitted
22:18:02 (2.32 KB/s) - `automatix2_1.1-2.2-6.10edgy_i386.deb' saved [205284/205284]

```

:confused:

---

### Post by rkakkar on 2006-12-07
i'm suspecting its the 70GB Fat32 partition size? people say fat32 should not be defined more than 32GB per partition...

---

### Post by taurus on 2006-12-07
Change the last value from 1 to 0!!!

---

