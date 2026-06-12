---
title: "Big GRUB problem"
date: 2009-04-20
forum: General Help
---

### Post by ac3raven on 2009-04-20
where to start.  I have 3 hard drives in my computer.

1x 320gb SATA
2x 160gb SATA's

I installed Fedora 10 on my 2x 160gb hard drives, which are configured as a RAID 0.  That installation went smoothly, I was very happy that Fedora automatically recognized my RAID, where as Ubuntu *still does not*.

Anyway, after a while I decided to format my 320gb and install Ubuntu 8.10 on it, with the intention of dual-booting.

Except that after I installed it, I got GRUB Error 17.  I magically fixed that somehow, only to get a different error message, Grub error 22.

After tinkering with grub commands to change the root partition, the location of stage1, and the setup command, I fixed grub on the 320, but when I try to boot from the raid array, I still have error 22.  I've confused myself thoroughly with the partitions, the device map, and all that.  So I'll explain as best as I can.

here is my device map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde

here is my menu.lst entry for Ubuntu:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a9dcc5f7-8d3e-4f5d-a654-1fb686fbbc07
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9dcc5f7-8d3e-4f5d-a654-1fb686fbbc07 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
root 		(hd0,5)
quiet

according to gparted, my 320gb is sdc, and my raid array is sda.

I tried changing the root to hd0 but that didn't do much of anything.

I need a way to get into my fedora installation.  If you need more info, I'll be glad to provide, but I just need a starting point (one that doesn't erase my fedora installation).

---

### Post by ajgreeny on 2009-04-20
> where to start.  I have 3 hard drives in my computer.

here is my device map:

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
So which is it, 3 hard disks or 5, or are you muddling up partitions and disks?
Which linux install is your grub running from, Fedora or Ubuntu?
Have you tried reinstalling grub from the other of your two linux OSs?

> title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		a9dcc5f7-8d3e-4f5d-a654-1fb686fbbc07
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9dcc5f7-8d3e-4f5d-a654-1fb686fbbc07 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
**root 		(hd0,5)**
quiet
Is ubuntu really on the first hard disk, partition 6, ie sda6, which is what this grub stanza shows it to be?

---

### Post by ac3raven on 2009-04-20
I have 3 hard disks, all the others are just external disks and flash drives.  The raid array disks that I have fedora on are sda and sdb, and the one I have Ubuntu on is sdc.

fdisk -l for sda and sdc:

/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       38914   312375892+  8e  Linux LVM

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000473fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38158   306504103+  83  Linux
/dev/sdc2           38159       38913     6064537+   5  Extended
/dev/sdc5           38159       38913     6064506   82  Linux swap / Solaris

I went ahead and reinstalled Ubuntu, now I have clean partitions.  I installed GRUB on sda (my fedora hard disks), and now when I boot from the raid array (the default), I get error 17.  Here's my new menu.lst:

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d89ce01d-a8e9-4f8e-bc1c-a5cd56810802
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d89ce01d-a8e9-4f8e-bc1c-a5cd56810802 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

Should I had a root parameter to the entry specifying the disk and partition I want, and if so, which one do I want?

---

### Post by ajgreeny on 2009-04-21
I know nothing about raid array and disk use for that, so can't help on that front, but grub error 17 means that the partition pointed at by grub can not be found.  So two comments:-

1.   Is the UUID in your grub menu.lst correct for ubuntu according to ```
sudo blkid
``` run from ubuntu live CD if needed?

2.   If you use the older grub menu format for the second line in the stanza shown of ```
root        (hd2,0)
```instead of the newer format you show (uuid        d89ce01d-a8e9-4f8e-bc1c-a5cd56810802) it may just work.  Make sure you get the partition correct, of course.

 From ubuntu 8.10, ubuntu has a filesystem inode size of 256 instead of 128 , and this new line format will not work with the older grub which fedora may have.  I found this by accident when trying ubuntu 8.10 on a second disk but keeping the 8.04 grub as the system boot manager.  Copying the stanza from the 8.10 grub menu.lst to the 8.04 menu.lst resulted in a no go situation.  Changing the format of that one line got it all to work.

---

### Post by ac3raven on 2009-04-22
```
/dev/sda1: LABEL="/boot" UUID="623adbe9-f99e-423d-89c8-40eda39ed608" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="d89ce01d-a8e9-4f8e-bc1c-a5cd56810802" SEC_TYPE="ext2" TYPE="ext3" 

```

That's by blkid result for sda and sdc.

Am I correct, You want me to replace my uuid line in the menu.lst entry, with the following code?
```

root		(hd2,0)
```

---

### Post by ajgreeny on 2009-04-22
Well, sdc1 is hd2,0 in grub-speak so it is worth trying.  You can do it in the grub menu on the fly if you choose that OS from the grub menu and hit "e" to edit, then go to the second line and hit "e" again.  Delete that line and replace it with** root  (hd2,0)** and hit enter then "b" to boot.  With luck it will work.  If so edit, the menu.lst file permanently with gedit as root

---

### Post by ac3raven on 2009-04-22
didn't do a thing.

---

### Post by ajgreeny on 2009-04-23
OK, sorry then, but I think I'm beaten on this problem.  Perhaps it's the raid setup that causes the difficulty.  The only other suggestion is to try all of the possible root (hd#,#) possibilities in the same way I showed you and see if you can find the correct one.

---

