---
title: "Cannot write to ext3 sata hard drive."
date: 2006-08-19
forum: Desktop Environments
---

### Post by blindluck48 on 2006-08-19
I have 320 gig Seagate SATA hard drive. I have it formatted as ext3. It's dev point is /dev/sda1 and it's mount point is /media/sda1.

Here is a copy of my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0
#root partition

/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1

#kubuntu install
/dev/hdb1       /media/hdb1     ext3    defaults        0       2

#crossover
/dev/hdb4       /media/hdb4     vfat    defaults,utf8,umask=007,gid=46 0       1

#Storage
/dev/sda1       /media/sda1     ext3    rw,auto,umask=77,gid=1000,       0       2

#swap
/dev/hdb2       none            swap    sw              0       0

#cdrom
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I'd like to give read/write permissions to all users and all groups.
How do I accomplish this?

TIA!

---

### Post by em3raldxiii on 2006-08-20
Mmm ... I could be very wrong here, but it's worth a shot.  I think it has to do with this part in your sda1:
 
```

umask=77

```
 
I think you want that to be 777 to enable read/write to all users.
 
Now, GID is much the same.  I think 1000 is ROOT, though I cannot be totally sure so I encourage those who know for sure to intervene.  
 
Let me know if I was any help at all :D ... it was more a pseudo edumacated guesstimate than anything else. ;)

---

### Post by beameup on 2006-08-20
I had logged into nautilus as root for a second drive I had added and made it read write and execute to all by right clicking on the drive in the "Computer" window and selecting properties, then selecting the appropriate checkboxes. Guess I should leave off the execute part.

---

