---
title: "can't access a partition"
date: 2009-03-11
forum: General Help
---

### Post by broken sword on 2009-03-11
A lil help please.

Just purchased a 500gb drive after my original 200GB drive died.

I re-installed and formatted my partition as follows:
48GB system partition
2GB swap
218GB ext3 partition
224GB ntfs partition

fdisk -l:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008dc86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5976    48002188+  83  Linux
/dev/sda2            5977        6225     2000092+   5  Extended
/dev/sda3            6226       32333   209712510   83  Linux
/dev/sda4           32334       60801   228669210    7  HPFS/NTFS
/dev/sda5            5977        6225     2000061   82  Linux swap / Solaris


/etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b1f4c1bf-98aa-4b0e-a6a9-7c14ba20e59d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=fde199c5-e907-46a1-ba86-84e1150b6417 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda4	/media/datadrive	auto	user,auto,exec,rw,sync	0	0
/dev/sda3	/media/vmdrive	ext3	user,auto,exec,rw,sync	0	1


I can't write to sda3, can someone tell me what I did wrong?

---

### Post by cariboo on 2009-03-11
IF you are not worried about other people accessing the drive you can set the permissions of the mount point to world read/write, by entering the following command in a terminal:

```
sudo chmod -R 777 /media/vmdrive
```

Jim

---

### Post by taurus on 2009-03-11
Or just change the ownership of /media/vmdrive from root to your login name, _assuming_ your login name is sword.

```
sudo chown -R sword:sword /media/vmdrive
ls -la /media
```

---

### Post by broken sword on 2009-03-12
that you for the responses.  I tried:

chmod -R 777 /media/vmdrive

that worked.  tho why did i have to do that? I'd used fstab to set permissions on that folder.

---

