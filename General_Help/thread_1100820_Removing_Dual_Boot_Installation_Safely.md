---
title: "Removing Dual Boot Installation Safely"
date: 2009-03-19
forum: General Help
---

### Post by bbarcelo on 2009-03-19
I currently have Ubuntu 8.10 and XP installed on a single hard drive where the partition table looks like this (from gparted, sudo apt-get install gparted if you're looking for an easy way to view your partitions):
```
/dev/sda1     ntfs      boot
/dev/sda2     extended
     /dev/sda3     ext3
     /dev/sda4     linux-swap
```
notes: I didn't include the mount points and boot on line #1 refers to the boot flag set on the primary partition.

So it's time to wave goodbye to Windows XP as I no longer have any use for it and want to remove it so I can use that HD space. I just want to format that NTFS partition to EXT3 and mount it in /media. Is there anything that stop me from just formatting the partition in gparted to EXT3? (note: Ubuntu is my default OS right now, so I don't believe I'd need to edit GRUB, correct?)

---

### Post by prince_niceguy on 2009-03-19
OK.. so here is what you need to do...

login into live cd. format the windows partition to your favorite linux filesystem type (ext3, reiserfs or xfs). if confused go with ext3 :-).

now follow this [thread]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub. after login into ubuntu from the hard disk and modify fstab to include your new parition.

that should work, i have messed my mbr lot of time and have recovered it n number of times... ;-)

---

### Post by meierfra. on 2009-03-19
> /dev/sda1     ntfs      boot
/dev/sda2     extended
     /dev/sda3     ext3
     /dev/sda4     linux-swap

Are you sure? Logical partition are  supposed to be numbered  5 and higher. Please post the output "sudo fdisk -lu"


> now follow this thread to reinstall grub. a

If  your ntfs partition is indeed on /dev/sda1 and you just format /dev/sda1 to ext3,  you neither  have to reinstall  grub nor edit menu.lst.

---

### Post by bbarcelo on 2009-03-20
> **meierfra. said:**
> Are you sure? Logical partition are  supposed to be numbered  5 and higher. Please post the output "sudo fdisk -lu"




If  your ntfs partition is indeed on /dev/sda1 and you just format /dev/sda1 to ext3,  you neither  have to reinstall  grub nor edit menu.lst.

My mistake, I just put numbers in, they're >5 in my fdisk/gparted partition view though. My NTFS partition is on /dev/sda1 though and, per your advice, I think I will just format it to EXT3.

---

### Post by meierfra. on 2009-03-20
> I think I will just format it to EXT3.

OK. Good luck.

---

