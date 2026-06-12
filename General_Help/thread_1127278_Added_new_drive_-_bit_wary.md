---
title: "Added new drive - bit wary"
date: 2009-04-16
forum: General Help
---

### Post by happyhacker on 2009-04-16
I've added an old drive (80Gb) to my second IDE bus (which also has a CD R/M installed) so it's not on hda bus which is on it's own. I hav'nt specifically done anything like mounting these unless Ubuntu has done that auto. It has some old PC stuff on it. Firstly, when I restarted the PC and looked in webmin (Partitions on local disks), I see it has seen it as a SCSI device B which is odd as I thought this was an IDE bus!

That screen also shows 1 partition 74.53Gb. If I go click on it's device name (SCSI device B) it shows up as having 4 partitions 15.69Gb each. If I try to edit IDE params I get a 404 page. But I guess this is because it is not mounted.

From that preamble, I want to format the whole drive and use it for backups to free up the nearly full hda. This is what the disk & network filesystem page shows after reboot:

Mounted as    Type    Location    In use?    Permanent?    
/proc Kernel Filesystem (proc) proc Yes Yes 
/ (Root filesystem) Linux Native Filesystem (ext3) Partition with ID c161af8b-b2f4-423e-b2ae-71af23ebae6b Yes Yes 
Virtual Memory Virtual Memory (swap) Partition with ID 9b517aad-19cd-4fd4-be04-8cc6bac0a3d9 Yes Yes 
/media/cdrom0 UDF,ISO9660 /dev/scd0 No Yes 
/lib/init/rw RAM Disk (tmpfs) tmpfs Yes No 
/sys SYSFS sysfs Yes No 
/var/run RAM Disk (tmpfs) varrun Yes No 
/var/lock RAM Disk (tmpfs) varlock Yes No 
/dev RAM Disk (tmpfs) udev Yes No 
/dev/shm RAM Disk (tmpfs) tmpfs Yes No 
/dev/pts PTS Filesystem (devpts) devpts Yes No 
... /fs/fuse/connections FUSECTL fusectl Yes No 

How do I get this drive properly mounted?

---

### Post by ajgreeny on 2009-04-16
Show us the output of ```
sudo fdisk -l
``` and we can probably help more.  I suspect it will be easy enough to delete the current partitions on the disk, make a new ext3 partition and either mount it at boot with a line in /etc/fstab. or keep it unmounted until you want to do it manually.

---

### Post by happyhacker on 2009-04-16
> sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xede2ede2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546   83  Linux
/dev/sda2            4788        4998     1694857+   5  Extended
/dev/sda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73696420

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      119512      153402   272218546+  20  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       82801      116350   269488144   6b  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?       33551      120595   699181456   53  OnTrack DM6 Aux3
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *       86812       86813       10668+  49  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by ajgreeny on 2009-04-16
If there is nothing on the disk you want or need I suggest you reformat the whole thing using gparted either using the live CD or install it to your hard disk ubuntu.  Delete the partitions on it at the moment and then make a new ext3 partition to use in ubuntu.  It looks as if the whole disk's partition table has become corrupt, and is causing these difficulties.

---

### Post by happyhacker on 2009-04-20
Yes, I want to wipe the drive. I seem to have a program called "parted". Is that the same? I want to use the disk for backups of windows PCs on our network and to keep a copy of the Ubuntu install (a full system so I can restore it (move the drive) on another PC. Should I create more than one partition and what should the partition(s) file type be (ext3?)?

PS I should add that it seems I have "SCSI device A" 40Gb and "SCSI device B" 79Gb (the disk I've added). Does being SCSI still mean I can use these independently?

When I go to create a primary partition in Webmin it is asking for the "start 1 to end 9727". How do I know this is going to use the full extent of the disk?

---

### Post by happyhacker on 2009-04-29
Now a bit more advice please (I'm frightened of doing something with sda!).

I have executed:
> sudo fdisk /dev/sdb

[COLOR="Blue"]The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): Command (m for help): Command (m for help): 
got EOF thrice - exiting..[/COLOR]

The disk is an 80Gb in size. PS I have server 8.10 and work via Webmin command line. I have installed gparted.

I was expecting to be given a list of commands and to select to partition the disk. Waht do I do with the above which seems to point to an error?

---

### Post by happyhacker on 2009-04-29
I've tried to play with this disk but fdisk will not do anything with it. I have tried fdisk /dev/hdb and gives

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): Command (m for help): Command (m for help): 
got EOF thrice - exiting..

Can someone give me a command that will wipe the disk of all partitions so I can install one partition (not OS disk)? I have tried various but always balks.

Failing this I can throw the disk away as I have a 3.5" disk (80Gb) with an adapter which I could use. Will this disk work with linux?

---

### Post by happyhacker on 2009-05-05
I have now got the disk recognised. It is sdb and has a GUI version of Ubuntu on it as I took it from a Linux laptop. It is on the same PCI bus as the DVD drive (No.2).

Can someone give me the scripted (full command line) version (Webmin does not allow interactive commands) to change/delete the 3 partitions? I want one large partition (at least that's what I assume is best) so I can use it for local backups as well as storing the local system image.

I haqve parted and fdisk commands available.

---

### Post by Grenage on 2009-05-05
Hi there,

Ok, so let's say you've run "fdisk /dev/sdb".  You're now in fdisk:

Press P to view current partitions, then..
Press D to delete one of the partitions, then enter the number of the partition you wish to delete.
Delete the remaining partitions.
Press N to create a new partition.
Press T to change the type of the partition (I believe you'll want 83 for ext3).
Press W to write the changes and exit.

Now to format your partition:

mkfs.ext3 -b 4096 /dev/sdb1

Now let's assume you want to automatically mount the drive every time the machine boots up.  First create a mount point:

mkdir /mnt/backup (replace backup with whatever you wish to call the point).  Mount points can be anywhere, but I recommend sticking with /mnt.

Edit fstab:

vim /etc/fstab (or if you prefer GUI text editing, gedit /etc/fstab).

Add your new entry:

/dev/hdb1               /mnt/backup                     ext3    defaults        1 1

Get fstab to run and check for errors with:

mount -a

Now anything placed in /mnt/backup is written to your disk, create a link on your desktop if you so wish:

ln -s /mnt/backup ~/Desktop/LINKNAME (replace LINKNAME with whatever you want your shortcut to be called).

---

### Post by happyhacker on 2009-05-05
Thanks, I done that now. I also discovered that Webmin makes it child's play by going to the "partitions on local disks" and the whole lot can be done with a few clicks. I have now got the disk mounted under home/backup as that's what i want it for. I guess if someone thinks that's silly I can move it.

---

### Post by Grenage on 2009-05-05
No harm in it being there, a lot of people do mount drives in their home directory.

Glad you got it working.

---

