---
title: "Gparted partition not seen - do I need to mount it?"
date: 2005-12-08
forum: General Help
---

### Post by Jaylon on 2005-12-08
Hello.

I've tried to create a partition in gparted to use for my data. The partition is showing in gparted as hda8, but it is not showing up in the filesystem.

Do I now need to mount the partition to make it available? If so, could you show me the instructions?

I have seen fstab mentioned in some posts although I don't know what to do with it- my fstab file is below.

Thanks, Jay

```
/etc/fstab: static file system information.

<file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda5       /media/hda5     vfat    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  ext,vfat    rw,user,noauto  0       0
```

---

### Post by az on 2005-12-08
Yeah, the disks gui tool can mount a partition, but it does notwrite to fstab so that it is permanent.

You would have to add a line in fstab for your partition.  For example, if is is hda8 then

/dev/hda8       /storage     vfat    defaults        0       0

You would have to create a directory for it

sudo mkdir /storage
Call it whatever you want.

If youmade it a linux partition (ext3) then change the vfat to that on the line you add to fstab.

Once you change your fstab, you can mount it by running

sudo mount -a

---

### Post by Jaylon on 2005-12-08
Thanks a lot, that seems to have sorted it out. 

For other people reading, I think you have to create the folder in media, so it's /media/storage or whatever. This is what worked for me anyway.

---

### Post by az on 2005-12-08
[QUOTE=Jaylon]Thanks a lot, that seems to have sorted it out. 

For other people reading, I think you have to create the folder in media, so it's /media/storage or whatever. This is what worked for me anyway.[/QUOTE]

I think it is a good idea to put it in Media, but you can put it anywhere you like.

Just like anoter volume (disk) can hold your /home or /var partition and are mounted in the / (root) directory.

I do not know if /media is part of the filesystem hiearchy.  It may....

---

### Post by Bachstelze on 2005-12-08
Of course it is. In linux, EVERYTHING is part of the filesystem.

---

### Post by az on 2005-12-08
[QUOTE=HymnToLife]Of course it is. In linux, EVERYTHING is part of the filesystem.[/QUOTE]

Oops.  I meant "Filesystem Heirarchy Standard".


Edit:  I looked it up:


"/media : Mount point for removeable media
Purpose
This directory contains subdirectories which are used as mount points for removeable media such as floppy disks, cdroms and zip disks."

[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT)

Since this is not a removable disk, but a partition on your HD, I do not know what the standard is.  Like I said.  I do not think it is a bad idea to put it there.

---

