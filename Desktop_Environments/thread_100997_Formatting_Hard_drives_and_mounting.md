---
title: "Formatting Hard drives and mounting"
date: 2005-12-08
forum: Desktop Environments
---

### Post by djgenesis on 2005-12-08
Hello guys..
I have a system Intel P4 1.4GHz with 3x40Gb hard drives and a CD-rom.
The IDE settings are
IDE1 --> Master (hard drive 1)
      --> Slave (Hard drive 2)

IDE2 --> Master (CD ROM)
       --> Slave (Hard Drive 3)

I am running the Hoary Hedgehog on HD1 and the other 2 are old NTFS systems.

How can i format the other two? 
I have been looking around and I got to as far as viewing the devices with:

```
 sudo fdisk -l 
```
All is clear here... But.. when i format them... will i have to specify the start/end cylinders? How can i skip this step? And how can i find more info in formatting like that if i want to try something "dangerous" when i feel confident?

Thanks

---

### Post by kairu0 on 2005-12-08
Run fdisk 2 times (once for each drive):

```
sudo fdisk /dev/hdb
sudo fdisk /dev/hdd

```

Once in fdisk, delete all partitions and set up a new one. When you go to create a partition I believe the default is to use all unused cylinders so it should set that part for you.

Then you just have to format with ReiserFS tools or the tool for whatever file system you want to install on them.

---

### Post by djgenesis on 2005-12-09
Thanks man, that seemed to work.
But from ReiserFS i only have the ReiserFSck and ReiserFStune. None of them refer to formatting and there are no more on synaptic. Can't i just mount it as is? And if not, what other tools are there?

Thanks again

---

### Post by kairu0 on 2005-12-10
You can't mount your partitions "as is" because they are not formatted yet. You have blank partitions with a "Reiser" label on them is all.

Format them with:

# sudo mkreiserfs /dev/hdb1

for example.

---

### Post by djgenesis on 2005-12-10
Hmmm... after the mkreiserfs i tried this:

```
genesis@ubuntuj:~$ sudo fdisk -l
```

and i got this:

```

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4770    38314993+  83  Linux
/dev/hda2            4771        4863      747022+   5  Extended
/dev/hda5            4771        4863      746991   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdb doesn't contain a valid partition table

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdd doesn't contain a valid partition table

```

That can't be good huh? :o

---

### Post by djgenesis on 2005-12-10
mmm.. wait ... i was doing something wrong here.
I was performing mkreiserfs to /dev/hdb NOT /dev/hdb1. So i rerun fdisk to erase all the partitiions i had created and created new ones:
/hdb1
/hdd1 
then i applied ```
 sudo mkreiserfs /dev/hdb1 
```
```
 sudo mkreiserfs /dev/hdd1 
```

Then i mounted the hard drive to /mnt with 

```
 sudo mount /dev/hdb1 /mnt/tmp 
```

and it is working now :D Thanks.

Just a couple more things.

1) How do i mount to a specific place? Ideally that would be in Places -> Computer or...... i dunno.. where do most people mount so it can be useful? and 
2)How do i mount at startup without having to do it manually every time?


Again thanks for all your help

---

### Post by kairu0 on 2005-12-10
In that case, you still have to create the partitions before formatting.

Someone please correct me if I'm wrong, but I assume that a blank drive will return that "no partition table, stupid" message.

Anyway, partition your hard drive:

```

sudo fdisk /dev/hdb

```

Once in fdisk, type "n" to create a new partition, choose your type and size. Now, type "w" to write the partition table to disk. Reboot, format the new partition, and swirl whiskey.

---

### Post by djgenesis on 2005-12-10
Did that... Didn't have to reboot though... 

> 

and it is working now  Thanks.

Just a couple more things.

1) How do i mount to a specific place? Ideally that would be in Places -> Computer or...... i dunno.. where do most people mount so it can be useful? and
2)How do i mount at startup without having to do it manually every time?



---

### Post by kairu0 on 2005-12-10
To change mount locations and mount automatically, it is best to edit your /etc/fstab file ("sudo gedit /etc/fstab"). Here is mine. Everything except the cdrom and the usb drive mount automatically (notice the "noauto" part.)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               reiserfs notail          0       1
/dev/hda6       /media/library reiserfs defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1	/media/usb	auto	rw,user,noauto	0	0

```

Once you get that taken care of, open up the Nautilus file manager, open up the mounted folder (in my case "/media/library") and Add it to the Bookmarks menu. Now, it will appear in your Places list.

---

### Post by djgenesis on 2005-12-12
Thanks a lot for all your help ! :D 
You're a star! :KS

---

