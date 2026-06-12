---
title: "how do i format a sd card?"
date: 2007-04-12
forum: Desktop Environments
---

### Post by k0mpresd on 2007-04-12
how do i format an sd card to an ext2 file format?

---

### Post by rmemm on 2007-04-13
I have not tried this -- but I assume you do it the same way you do a hard disk.  Just be real careful you know which block device is the memory card.  By this I mean -- don't accidently reformat your hard drive or something.

In general -- there are a couple of way to do formatting.  There is the command line way which uses mke2fs (see man mke2fs) and there is gparted which is a nice gui program.

You'll have to decide if you want to partitian the device (probably no?) or just write the file system directly.  A command line partitioning tool is fdisk (see man fdisk) or gparted does this also.  Same caution applies to using fdisk -- be real careful you know which block device is the one you want to modify.

One thing I will say -- not sure why you want ext2 on an sd card.  Cameras for example won't understand ext2, only linux will. 

Rob

---

### Post by jetpeach on 2008-01-01
in qtparted or gparted (both are very similar, one for gnome other for kde) it is very easy to format and the gui lets you pick what type of filesystem and options.
install using "sudo apt-get install [qt or g]parted"
i also found this gave me better success than some terminal commands for correctly formatting my 2gb cards to 2gb instead of 1gb. i never knew why, but qtparted formated them 2gb and the terminal commands i tried (such as, "mkdosfs -c -F 32 -n 2GBDisk -s 64 -S 512 -v /dev/sda1") were all only yielding 1gb... somebody said something about some cards having multiple components or something, but i'm just glad qtparted worked without worrying about why or details...

---

