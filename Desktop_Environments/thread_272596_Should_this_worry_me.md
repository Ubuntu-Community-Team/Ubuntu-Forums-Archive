---
title: "Should this worry me?"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Whhpssh on 2006-10-06
I installed a new hard drive last week and then reinstalled Ubuntu.  I let the installer partition the new 80GB drive I installed and I assumed it also formatted all partitions.  I noticed this today, though.

Boot Partition:
[IMG]http://img.photobucket.com/albums/v209/Whhpssh/part1.jpg[/IMG]

Main Partition (I assume):
[IMG]http://img.photobucket.com/albums/v209/Whhpssh/part5.jpg[/IMG]


Should I worry about partition 5 being inaccessible and unformatted?  I haven't had any issue saving files to the drive so everything seems to be working fine.

Thanks for any information you can give me.  I know all about formatting and partitioning but I learned it in the DOS and Windows world so this is a little foreign to me.

---

### Post by Kateikyoushi on 2006-10-06
Interesting. What is the output of this command ?

```
sudo fdisk -l
```

---

### Post by astoltz on 2006-10-06
It looks to me like you are using 243 Meg of your new disk to mount partition 1 at /boot.  The rest of your disk (64 Gig) is not being used at all.  The question then is where is he rest of your Ubuntu installation? What does your /etc/fstab look like?

---

### Post by Kateikyoushi on 2006-10-06
I guess the rest is on the other hdd, but we will know for sure if he answers.

---

### Post by Whhpssh on 2006-10-06
> **Kateikyoushi said:**
> Interesting. What is the output of this command ?

```
Output:

me@ubuntubox:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32        9729    77899185    5  Extended
/dev/hda5              32        9729    77899153+  8e  Linux LVM
me@ubuntubox:~$
```



[quote=astoltz]It looks to me like you are using 243 Meg of your new disk to mount partition 1 at /boot. The rest of your disk (64 Gig) is not being used at all. The question then is where is he rest of your Ubuntu installation? What does your /etc/fstab look like?[/quote]

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```



[QUOTE=Kateikyoushi]I guess the rest is on the other hdd, but we will know for sure if he answers.[/quote]

Single HDD system.  That's the other thing I thought was weird.  I don't understand why it's showing two HDDs when there's only one.

---

### Post by astoltz on 2006-10-06
Ahhh! You have an encrypted filesystem.  Don't know much about it but that line for /dev/mappper/Ubuntu-root is the encrypted part.  It must show up as unused space when you look at it with regular disk tools.

---

### Post by Whhpssh on 2006-10-07
> **astoltz said:**
> Ahhh! You have an encrypted filesystem.  Don't know much about it but that line for /dev/mappper/Ubuntu-root is the encrypted part.  It must show up as unused space when you look at it with regular disk tools.


Gotcha.  Thanks for the help.  I feel much better now.  :D

---

