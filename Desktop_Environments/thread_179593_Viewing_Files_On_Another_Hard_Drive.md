---
title: "Viewing Files On Another Hard Drive"
date: 2006-05-20
forum: Desktop Environments
---

### Post by robcarr2 on 2006-05-20
Hey, I am going to install linux, but I have another hard drive ( that wont have linux on ) which is fat32, would I be able to browse the files on this hard drive through ubuntu?

---

### Post by Carbonbasedmistake on 2006-05-20
You can view your fat 32 harddrive space in Ubuntu. You can do it a number of ways. First create a mount point (a directory) such as /mnt/windows. You can then go to a terminal window and issue as su:

mount -t vfat /dev/hdax /mnt/windows     (where x is your windows drive)

You can then use the file manager to view the contents of /mnt/windows as the contents of the fat 32 harddrive.

To automatically add the fat 32 drive edit the /etc/fstab with the data for the drive and on boot it will mount the windows drive.

hope this helps

bob

---

### Post by robcarr2 on 2006-05-20
i understnad the mount -t vfat /dev/hdax/

but I am a bit confused on the /mnt/windows bit, I know that is like a directory, but do you meen I enter were I want the root to be there? e.g. if I had a folder in the root of my hard drive called Test, I would use /Test as the mount point?

If this is what you meen to view EVERYTHING on the hard drive would i set the mount point as /

---

### Post by Ramses de Norre on 2006-05-20
In Linux you have / and all other partitions are mounted somewhere under it. This places where they are mounted are called mount points and are just directories. So you'll need to create a directory to mount the fat partition at. When it's mounted you can browse the mount point and everything on the partition will apear in that folder. You see how it works when you've done it once ;)

So in terminal do ```
sudo mkdir /media/mountpoint
sudo mount /dev/hda1 /media/mountpoint -t vfat -o iocharset=utf8,umask=0000
``` Change mountpoint to another name if you want.
/dev/hda1 is the device node of your drive, hdxy for a ide drive, x=a,b,c,d for first master, first slave, second master, second slave. y= number of partition on the drive (so first partition on secondary master = hdc1)
For sata drives: sdxy with same logic, x= number of sata connector.

To mount it everytime at bootup do this: ```
sudo gedit /etc/fstab
``` And add a line like this at the end: ```
/dev/hda1       /media/mountpoint  vfat iocharset=utf8,umask=0000 0 0

``` Change mountpoint and device node the same way.

Then do ```
sudo mount -a
``` to mount all partitions in fstab. (happens automaticaly on every boot up)

---

### Post by robcarr2 on 2006-05-20
[QUOTE=Ramses de Norre]In Linux you have / and all other partitions are mounted somewhere under it. This places where they are mounted are called mount points and are just directories. So you'll need to create a directory to mount the fat partition at. When it's mounted you can browse the mount point and everything on the partition will apear in that folder. You see how it works when you've done it once ;)

So in terminal do ```
sudo mkdir /media/mountpoint
sudo mount /dev/hda1 /media/mountpoint -t vfat -o iocharset=utf8,umask=0000
``` Change mountpoint to another name if you want.
/dev/hda1 is the device node of your drive, hdxy for a ide drive, x=a,b,c,d for first master, first slave, second master, second slave. y= number of partition on the drive (so first partition on secondary master = hdc1)
For sata drives: sdxy with same logic, x= number of sata connector.

To mount it everytime at bootup do this: ```
sudo gedit /etc/fstab
``` And add a line like this at the end: ```
/dev/hda1       /media/mountpoint  vfat iocharset=utf8,umask=0000 0 0

``` Change mountpoint and device node the same way.

Then do ```
sudo mount -a
``` to mount all partitions in fstab. (happens automaticaly on every boot up)[/QUOTE]

Works like a charm ;)

---

