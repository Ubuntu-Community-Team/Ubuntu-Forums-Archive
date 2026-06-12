---
title: "Mount Error"
date: 2006-07-19
forum: Desktop Environments
---

### Post by RexInTheCity on 2006-07-19
I have an 80GB SATA hdd formated in Fat32 so I can access it in both Ubuntu and windows. I just went to Places > Computer and it's listed, so I clicked on it and get this error.

Unable to mount the selected volume.
error: device /dev/sdb1 is not removable
error: could not execute pmount

I havn't used linux since last summer so I'm a little rusty and could use some help ](*,)

---

### Post by orlox on 2006-07-19
Did you try doing mounting it from a terminal? I think the command was something like:

sudo mount -t vfat dev/sdb1 <place where you want to mount it...>

and the place where you mount it must exist...At least I have a Sata disk and I mount the partitions this way.

---

### Post by RexInTheCity on 2006-07-19
> **orlox said:**
> Did you try doing mounting it from a terminal? I think the command was something like:

sudo mount -t vfat dev/sdb1 <place where you want to mount it...>

and the place where you mount it must exist...At least I have a Sata disk and I mount the partitions this way.

I created a folder called 80GB in the /mnt directory

$ sudo mount -t vfat dev/sdb1 /mnt/80GB
mount: special device dev/sdb1 does not exist

---

### Post by orlox on 2006-07-19
That's strange...are you sure that de hard drive is pointed by /dev/sdb1, or is i other device? Here I use mount on /dev/sdb1 wich points to nowhere on my machine and fails with the same error it gives you. When I use it on a partition located at /dev/sda3 thats FAT32 it works:

root@PCPABLO:/home/pablo# mount -t vfat /dev/sdb1 /home/
mount: special device dev/sdb1 does not exist
root@PCPABLO:/home/pablo# mount -t vfat /dev/sda3 /home/
root@PCPABLO:/home/pablo#

actually mounting it to home is a bad example cause It really made my filesystem bad, but the case is that the mount works when I use the correct device...

---

