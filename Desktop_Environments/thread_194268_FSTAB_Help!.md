---
title: "FSTAB Help!"
date: 2006-06-11
forum: Desktop Environments
---

### Post by mo_roodi on 2006-06-11
My apologies if this has already been posted. I can't seem to find anything on the forums that may help. Basically I have two partitions setup which I need to set RW access to for all users. I've included my fstab below. I would like to set read-write access for all users to /media/hdb1 and /storage. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /boot           ext3    defaults        0       2
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs umask=0        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     ntfs umask=0        0       0
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/sda1       /media/sda1     ntfs umask=0        0       0
/dev/hdb7       /storage        ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       
```

I've tried playing around with a few tags and even tried setting the noauto tag to see if when I mount it that might help (it was a workaround I found in Fedora Core while I was still on the dark side). No luck though ](*,).

Any help would be most appreciated. Cheers, 

Mo

---

### Post by bikeboy on 2006-06-11
I think a umask option will do the trick. I'm not the best with those but umask=0000 would mean 777 permissions so that full write/exec access is given to anyone (probably not a good idea), 0002 would mean 775 and so on.

---

### Post by RRS on 2006-06-11
Try;
```
/dev/hdb1    /media/hdb1 vfat iocharset=utf8,umask=000  0    0

```

---

### Post by mo_roodi on 2006-06-11
[QUOTE=bikeboy]I think a umask option will do the trick. I'm not the best with those but umask=0000 would mean 777 permissions so that full write/exec access is given to anyone (probably not a good idea), 0002 would mean 775 and so on.[/QUOTE]

That worked for the 2 fat32 partitions (It's ok that I give everyone access to those seen as there's nothing too important on there. They're just used for transferring information between Windows and Linux). What I need is for one user (namely myself) to have read/write access to the partition /dev/hdb7 which is mounted at /storage which is use for storing data. Like I said I've played around with the fstab file but I can't seem to figure it out. Any help would be welcome.

---

### Post by sanjose on 2006-06-11
when it is already mounted try
```
sudo chmod a+rw /storage since it is ext3
```

---

### Post by mo_roodi on 2006-06-11
Thanks sanjose, that did the trick... Don't know why I didn't think of that before. 
All working now. Cheers,

Mo

---

