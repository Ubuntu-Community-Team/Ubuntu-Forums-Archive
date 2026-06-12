---
title: "Formating a Sata hardrive"
date: 2008-12-24
forum: General Help
---

### Post by fbjoey on 2008-12-24
Hello
Over the weekend I replaced my ps3 hard drive and was left with a 40gb sata hard drive. I brought an enclosure for it and would like to format it to use as a portable hard disk drive but the disk that came with the enclosure obviously only supports windows and mac platforms. 
Can anyone help me format it?

Cheers.
Joe

---

### Post by fbjoey on 2008-12-24
bump

---

### Post by logos34 on 2008-12-24
you don't need the cd.  Format it ext3:

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by pietjanjaap on 2008-12-24
If external drive is not visible in nautilus them start terminal and type "lsusb", do this a few times. 
Normally this is not necessary, but im my 8.04 sometimes the harddrive is not visible.
Then install and start "gksu gparted", here you can format.

---

### Post by fbjoey on 2008-12-24
Thank it seems like it will work but i'm stuck.
 ```
Partition 1 is already defined.  Delete it before re-adding it.

```
I cant figure out how to delete the partition already left on there (I think this was left by the ps3)

---

### Post by logos34 on 2008-12-24
what does (in a terminal)

sudo fdisk -l

show?

---

### Post by fbjoey on 2008-12-24
Comes up with this...

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19076   153227938+  83  Linux
/dev/sda2           19077       19452     3020220    5  Extended
/dev/sda5           19077       19452     3020188+  82  Linux swap / Solaris

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0xdfdda4f6

Disk /dev/sdf doesn't contain a valid partition table

```

---

### Post by logos34 on 2008-12-24
You can try wiping the drive, then create a new partition table and partitions:

If gparted doesn't see it either, try:
> 
sudo dd if=/dev/zero of=/dev/sdf conv=notrunc

sudo fdisk /dev/sdf

command action:
> **o** create a new empty DOS partition table

then 

> **n**   add a new partition

make a new primary ext3 partition

---

### Post by fbjoey on 2008-12-24
I just realised I was typing the wrong logical name thing and now it started to work but I hit another bump in the road
```
First cylinder (1-38154, default 1): 1
Last cylinder, +cylinders or +size{K,M,G} (1-38154, default 38154): 1

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
fbjoey@Fr3d:~$ sudo mkfs -t fat32 /dev/sdf1
mkfs.fat32: No such file or directory
fbjoey@Fr3d:~$ sudo mkfs -t fat32 /dev/sdf1
mkfs.fat32: No such file or directory
fbjoey@Fr3d:~$ 
```

Does this mean its not recognising the drive it was recognising 5 seconds ago. I'm confused.

---

### Post by fbjoey on 2008-12-24
Sorry logos34 ignore my that reply but I did what you said and its seems to be working fine expect i create a fat32 so i can use it on windows as well.
```
Building a new Sun disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
contents won't be recoverable.

```

Its came up with this. Does it mean It worked?

---

### Post by logos34 on 2008-12-24
'1' is awefully small! try leaving 'Last cylinder' default--it'll make one big partition for the whole disk

---

### Post by albinootje on 2008-12-24
> **fbjoey said:**
> 
fbjoey@Fr3d:~$ sudo mkfs -t fat32 /dev/sdf1
mkfs.fat32: No such file or directory
fbjoey@Fr3d:~$ sudo mkfs -t fat32 /dev/sdf1
mkfs.fat32: No such file or directory
fbjoey@Fr3d:~$ [/CODE]

You probably want :
```

sudo mkfs.vfat /dev/sdf1

```

---

### Post by logos34 on 2008-12-24
run 

sudo fdisk -l

again

---

