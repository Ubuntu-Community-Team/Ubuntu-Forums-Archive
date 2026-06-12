---
title: "Bad Mounted Disk Name"
date: 2006-09-30
forum: Desktop Environments
---

### Post by waffen on 2006-09-30
I have a extrange name (Name and Volumen) for my VFAT disk in my Desktop: 

```

_PNG
001A

```


Some days its appear like: WindowsD

See my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/Windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/WindowsD     vfat    defaults,iocharset=utf8,umask=007,gid=46 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Any idea? ](*,) 

Thanks!

---

