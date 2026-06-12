---
title: "[SOLVED] drive not mounted automatically"
date: 2008-10-10
forum: Desktop Environments
---

### Post by koba101 on 2008-10-10
Hi,

Ever since I installed hardy again, I can't get my other hard disk to mount.  I've got two hard disks on my PC one which has the ubuntu installed on and the anoter NTFS hard disk.

Everytime i startup I have to manually mount the NTFS one.

When i first installed hardy, this didn't happen

---

### Post by WWSmith36 on 2008-10-10
Please post the output of these two command.
```

sudo fdisk -lu
cat /etc/fstab
```

Please put output in code box, its easier to read.
Thank you

---

### Post by koba101 on 2008-10-10
1.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006562a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   958582484   479291211   83  Linux
/dev/sda2       958582485   976768064     9092790    5  Extended
/dev/sda5       958582548   976768064     9092758+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x477e477d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976751999   488375968+   7  HPFS/NTFS

```


2.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=127251f2-4a78-4c8b-b5ef-3ef2c4635f89 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a22d74fc-0db0-423e-b320-b4da91d95991 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by WWSmith36 on 2008-10-10
Ok you just need to edit you fstab file to get it to automount for you

You can call put the mountpoint wherever you want.  I am using /media/Windows in this example.

```
sudo mkdir /media/Windows
gksudo gedit /etc/fstab
```

Add this line to the end of the file

```
/dev/sdb1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Save and exit.

---

### Post by koba101 on 2008-10-11
alright thanks

---

