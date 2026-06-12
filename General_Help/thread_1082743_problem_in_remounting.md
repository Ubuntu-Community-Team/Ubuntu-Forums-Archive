---
title: "problem in remounting"
date: 2009-02-28
forum: General Help
---

### Post by Mosa500 on 2009-02-28
i have a problem in remounting partition   /dev/sda1   fat32
i unmount it using gparted then format it to fat32
then went to terminal to write mount -a and mount /dev/sda1 and i also used
mount /media/sda1 but only i have the following message :

mount: special device /dev/disk/by-uuid/AD62-E846 does not exist

and the partition not remounted by rebooting
my etc/fstab show the following

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e8e33c36-eeb4-43e8-af3b-f6d0681670b2 /               ext3    defaults,erro$
# /dev/sda1
UUID=AD62-E846  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=99FA-072C  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=E472-3D7B  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=85FE-27CB  /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=b0b48cc1-9be8-46a8-b196-425cc1c90c29 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by dbbolton on 2009-02-28
> **Mosa500 said:**
> i have a problem in remounting partition   /dev/sda1   fat32
i unmount it using gparted then format it to fat32
then went to terminal to write mount -a and mount /dev/sda1 and i also used
mount /media/sda1 but only i have the following message :

mount: special device /dev/disk/by-uuid/AD62-E846 does not exist

and the partition not remounted by rebooting
my etc/fstab show the following

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e8e33c36-eeb4-43e8-af3b-f6d0681670b2 /               ext3    defaults,erro$
# /dev/sda1
UUID=AD62-E846  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=99FA-072C  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=E472-3D7B  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=85FE-27CB  /media/sda9     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=b0b48cc1-9be8-46a8-b196-425cc1c90c29 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
First make a backup of your current fstab:
```

sudo cp /etc/fstab /etc/fstab.original

```
Then you could try changing this line
```
UUID=AD62-E846  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
```
to this:
```

/dev/sda1 /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
```

---

