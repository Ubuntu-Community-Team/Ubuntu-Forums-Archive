---
title: "Can't get FSTAB to mount volume properly!"
date: 2009-01-02
forum: General Help
---

### Post by slicemaster on 2009-01-02
well, i am not particularly new to ubuntu but i can't get one of my partitions to mount properly for the life of me.

i have famerilised my self with FSTAB but cant seem to get the drive to mount with the access rights that i need.

Any ways, here is my FSTAB that ubuntu automaticly generated for me upon installation.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=80fd9208-c66f-471d-98ca-1c928258ff7e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=f577d3ff-d82a-48a3-b101-949e5f5fa8ea /media/data/    ext3    relatime        0       2
# /dev/sda3
UUID=14f9d605-88aa-42ed-92ee-d965a4b09958 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

i have played with various configuration options but have not been able to suceed. i am trying to make sda2 a full access partition where all users can mount/unmount the volume and read/write/change/and delete.

thanks for the help.

---

### Post by Tim Sharitt on 2009-01-02
Try adding users,rw to the options, which would make it
```
# /dev/sda2
UUID=f577d3ff-d82a-48a3-b101-949e5f5fa8ea /media/data/    ext3   users,rw,relatime        0       2
```

---

