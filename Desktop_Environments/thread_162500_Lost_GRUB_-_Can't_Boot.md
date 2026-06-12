---
title: "Lost GRUB - Can't Boot"
date: 2006-04-19
forum: Desktop Environments
---

### Post by Geffers on 2006-04-19
Owing to fiddling about with xosl (Operating System Loader) I've lost GRUB off my machine so am unable to boot ubuntu.

Is there any way round this eg, Linux rescue floppy/CD and any command line boot options.

Until I sort this no ubuntu :( 

Geffers

---

### Post by hw-tph on 2006-04-19
Use a livecd of some sort - the Ubuntu one or any minimal Linux livecd with kernel 2.6 should suffice to boot from. When the system is up and running from the CD, mount your Ubuntu partitions to (temporary) mountpoints and chroot into your Ubuntu system and run **grub-install /dev/hda** (if /dev/hda is your first drive).

Say that you have /dev/hda1 as your Ubuntu root partition and that you use OBP (One Big Partition) instead of splitting your disk into several smaller partitions. This is fairly common, perhaps even the default? Anyhow, this is what you would do:
```
mkdir /mnt/ubuntutmp
mount /dev/hda1 /mnt/ubuntutmp
mount -t proc none /mnt/ubuntutmp/proc
mount --bind /dev /mnt/ubuntutmp/dev
chroot /mnt/ubuntutmp /bin/bash
```
...and if that goes well:
```
grub-install /dev/hda
```
This assumes you haven't hosed your Grub configuration (/boot/menu.lst). If you have, you will have to write a new one or grab an example online and modify it according to your needs.

This was written off of the top of my head. If I messed something up, error messages will let you know. :)


Håkan

---

### Post by Geffers on 2006-04-19
[QUOTE=hw-tph]Use a livecd of some sort - the Ubuntu one or any minimal Linux livecd with kernel 2.6 should suffice to boot from. When the system is up and running from the CD, mount your Ubuntu partitions to (temporary) mountpoints and chroot into your Ubuntu system and run **grub-install /dev/hda** (if /dev/hda is your first drive).

[/QUOTE]

Think I followed that one.

[QUOTE=hw-tph]
Say that you have /dev/hda1 as your Ubuntu root partition and that you use OBP (One Big Partition) instead of splitting your disk into several smaller partitions. 
[/QUOTE]

Hmm, I've got 3 primary drives, Win98 on 2 of them, then an extended partition with two logical drives, a Linux swap and an Ext2


[QUOTE=hw-tph]
This is fairly common, perhaps even the default? Anyhow, this is what you would do:
```
mkdir /mnt/ubuntutmp
mount /dev/hda1 /mnt/ubuntutmp
mount -t proc none /mnt/ubuntutmp/proc
mount --bind /dev /mnt/ubuntutmp/dev
chroot /mnt/ubuntutmp /bin/bash
```
...and if that goes well:
```
grub-install /dev/hda
```
This assumes you haven't hosed your Grub configuration (/boot/menu.lst). If you have, you will have to write a new one or grab an example online and modify it according to your needs.

This was written off of the top of my head. If I messed something up, error messages will let you know. :)

Håkan[/QUOTE]

I'll give it a try; thanks for very prompt reply.

Geffers

---

### Post by Geffers on 2006-04-19
[QUOTE=hw-tph]Use a livecd of some sort - the Ubuntu one or any minimal Linux livecd with kernel 2.6 should suffice to boot from. When the system is up and running from the CD, mount your Ubuntu partitions to (temporary) mountpoints and chroot into your Ubuntu system and run **grub-install /dev/hda** (if /dev/hda is your first drive).
[/QUOTE]

Further to your reply, am I able to use to liveCD (Downloading now) to boot straight in to my ubuntu system, I can address the 'GRUB' issue later.

Geffers

---

### Post by Geffers on 2006-04-19
[QUOTE=hw-tph]Use a livecd of some sort - the Ubuntu one or any minimal Linux livecd with kernel 2.6 should suffice to boot from. When the system is up and running from the CD, mount your Ubuntu partitions to (temporary) mountpoints and chroot into your Ubuntu system and run **grub-install /dev/hda** (if /dev/hda is your first drive).

Håkan[/QUOTE]

Hope you don't mind but I'm going to post a similar question but ask how to boot my original system with the liveCD.

I'll pursue your advice to get GRUB back but initially I just want to be able to get my ubuntu going again, don't mind if it's floppy or CD as a temporray measure.

When I followed your advice and tried to mount /dev/hda3 /mnt/ubuntutmp it told me the mount point did not exist even though I could see it.

My Ext ubuntu partition is hda3 and the swap is hda7

Geffers

---

### Post by Geffers on 2006-04-21
This may be of interest to any others in a similar position.

[http://adrian15.raulete.net/grub/tiki-file_galleries.php](http://adrian15.raulete.net/grub/tiki-file_galleries.php)

I tried the Super Grub Disk Floppy and this would not instal so I went for the CD version and 'hey presto', I've got ubuntu back again =D> 

I took the 'Rescue' boot option which dumped me in to a command line mode, typed exit which then started the GUI :wink: 

So I've got it back, just need to sort out GRUB now... :???: 

Geffers

---

