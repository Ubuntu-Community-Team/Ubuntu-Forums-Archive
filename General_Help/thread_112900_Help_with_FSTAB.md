---
title: "Help with FSTAB"
date: 2006-01-05
forum: General Help
---

### Post by cetol on 2006-01-05
I hope this is the right forum, if not I beg forgiveness in advance! I edited my fstab to auto mount my window partitions. Now during boot-up I get a "failed" message on "mounting local filesystem" but all the partitions appear to be mounted. Here is the contents of the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto	0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto	0       0
/dev/fd0        /media/floppy0  auto    rw,user,auto	0       0
/dev/hda1	/media/win_gen	auto	rw,user,auto	0	0
/dev/hda2	/media/win_vid	auto	rw,user,auto	0	0
/dev/hda3	/media/win_aud	auto	rw,user,auto	0	0
/dev/hdb5	/media/win_prog	auto	rw,user,auto	0	0
/dev/hda6	/media/video	auto	rw,user,auto	0	0

Note that there were no errors prior to edit.
Any suggestions for a newbie?

---

### Post by localzuk on 2006-01-05
The thing I would ask is if the Windows partitions are formatted using NTFS or FAT32. If the prior change the auto to NTFS and change the rw to ro (as read write in ntfs is not enabled by default). If the latter I am stumped.

---

### Post by oakz on 2006-01-05
Another thing to look at: did you remember to create (mkdir) the new mount point directories under /media ?

---

### Post by cetol on 2006-01-05
All the mount pionts have been created. I can access all the files on the partitions. I just get an error during boot. All the window partitions are fat32. I originally used vfat in the description but thought that might be creating the error so I changed it to auto.

---

### Post by localzuk on 2006-01-05
Taking another look, I have just realised you have set fd0 to automount - this will cause an error for sure.

---

### Post by cetol on 2006-01-05
That did the trick. Must have deleted to "no" by mistake.

Thanks for the help

---

