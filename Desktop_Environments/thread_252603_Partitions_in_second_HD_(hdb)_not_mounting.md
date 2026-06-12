---
title: "Partitions in second HD (hdb) not mounting"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Onos on 2006-09-07
I finally got around to wiping the second HD I had previously had set up for dual booting (Win XP/Ubuntu).

I went into gparted and deleted the previous partitions (one each of NTFS and  FAT32, with a third partition as ext3 for backing up some files/burning CDs).

I created 3 new partitions, all ext3. I had some issues figuring out how to mount them, came across a tutorial that lead me to create mount points for them and then create entries in /etc/fstab.

The partitions are:

/dev/hdb1 --> /media/windows10GB (this is a dump for QEMU stuff I will do later)

/dev/hdb2 --> /media/movies (storage for media files)

/dev/hdb3 --> /media/music (storage for music) 


I made the mount points, and chmod to 777 for each of them.

Then in /etc/fstab:```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2

#20.5GB HDD (Primary Slave)
/dev/hdb1       /media/windows10GB   ext3    defaults   0       0
/dev/hdb2       /media/movies      ext3    defaults   0       0
/dev/hdb3	/media/music      ext3    defaults   0       0 

#DVD-ROM (Secondary Master)
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

So far, the only thing that mounts (and is visible to my file browser) is /dev/hdb1 on /media/windows10GB...

What am I doing wrong?

---

### Post by amo-ej1 on 2006-09-07
open a console and enter *sudo mount /media/movies* does that work or does that give errors ?  
Are you sure you formatted the drives ?

---

### Post by Onos on 2006-09-07
That did not work... but it turns out that changing the mount "pass" values for my hdb paritions did the trick:

(in /etc/fstab)
```

/dev/hdb1       /media/windows10GB   ext3    defaults   0       1
/dev/hdb2       /media/movies      ext3    defaults   0       2
/dev/hdb3	/media/music      ext3    defaults   0       3 
```

---

