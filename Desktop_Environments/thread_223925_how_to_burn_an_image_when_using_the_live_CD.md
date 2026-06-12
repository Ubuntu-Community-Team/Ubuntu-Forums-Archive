---
title: "how to burn an image when using the live CD?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by andytof47 on 2006-07-27
HI i have just downloaded an alternate dapper image to restore my GRUb boot loader, only thing is i am booting from the live cd (standard Ubuntu) now that i have the ISO how can i burn it?????:---)

---

### Post by dabang on 2006-07-27
As I don't have access to a life-CD right now, I don't know, if cdrecord is distributed with it. But if it is, then do the following:

First mount the partition where you stored the iso file, for example:
```
mount /dev/hdX /mnt
```

then burn the iso with
```
cdrecord dev=/dev/hdc /path/to/downloaded_iso_file.iso
```

Replace "/dev/hdc" with the path to your CD-burning device. This should be it.

---

### Post by OpsVentus on 2006-07-27
Hello Andy,

if it's just about installing Grub, have a look at this:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Cheers,
Bart.

---

