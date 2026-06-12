---
title: "NTFS Access"
date: 2006-09-22
forum: Desktop Environments
---

### Post by dont42panic on 2006-09-22
Hello Ubuntu friends,

I have recently installed Dapper on my fresh new Dell laptop. Installation was clean, fast and complete. Very satisfied. But......

I partitioned the hard drive and all is well. Can boot both into MS as well as Dapper. Alas, when I attempt to access the NTFS partition using Nautilus, I get the following error message:  

                         Unable to mount the selected volume                             
                         error: Device /dev/hdx is not removable.
                         error: Could not execute pmount.


Any help would be greatly appreciated.

Thanks in advance

---

### Post by alecjw on 2006-09-22
You need to do:
```
sudo mount -t ntfs /dev/hdxx /somefolder
```
remember to replace hdxx with the right name (Eg hdb3)and /somefolder with your mountpoint
Or to make it mount on bootup, add this line to /etc/fstab:
```
/dev/hdxx  /somefolder  ntfs  nodev,nosuid  0  2
```
or, to make booting faster, replace the last 2 with a 0 and the drive will not be checked for errors.

---

### Post by Pjotr123 on 2006-09-22
I am unsure whether my contribution will help you, but perhaps so in an indirect way. There it goes:

It so happens that I have installed Ubuntu on a new Dell Inspiron notebook today as well. Also in a dual boot configuration.

First I repartitioned the hard disk, using Gnome Partition Editor (Gparted live CD). 

The first thing that struck me was, that this disk was not a hda but an sda, because it is probably linked with a USB connection to the motherboard.

The second thing that struck me, was that Dell had put no less than three primary partitions on the disk. The first (sda1) was a very small FAT16 partition, then a big NTFS partition with Windows XP on it (sda2), and last a small FAT32 partition of a few Gb (sda3). A weird construction. I didn't like it.

So I burned an image of the NTFS partition on a DVD+R, destroyed all the partitions and created an active primary NTFS partition on sda1 (40 Gb) and gave it a boot flag. Then I created an extended partition out of the remaining 33 Gb, which I subsequently divided in a few logical partitions, one of them being an ext3 for Ubuntu.

Afterwards I put Ubuntu on the ext3 partition, and manually put a reference to Windows in the menu.list of Grub. Then I put the Windows image back, on the sda1. Then I found out that I couldn't boot into Windows anymore! Error message: hal.dll couldn't be found in the windows\system32 map.

The culprits were, it appeared after a long search, two wrong entries in the boot.ini file (on sda1). They pointed towards sda2, whereas Windows was now ofcourse to be found on sda1.

Then there was the problem of write access to NTFS. How could I change those entries? Not with Linux. Luckily there is the free Ultimate Boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) 

I booted with that disk, used an NTFS file editor on the disk to change the boot.ini on sda1, and lo and behold, I could boot into Windows again from Grub! Also I could read (not write) NTFS files using Ubuntu.

Hope this helps you a bit in a roundabout sort of way.

Greeting, Pjotr.

---

