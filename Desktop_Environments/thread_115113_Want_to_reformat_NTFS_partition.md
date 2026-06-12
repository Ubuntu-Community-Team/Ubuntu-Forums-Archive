---
title: "Want to reformat NTFS partition"
date: 2006-01-09
forum: Desktop Environments
---

### Post by gnuconvert on 2006-01-09
I installed Breezy Badger on my former Windows 2000 machine as a dual boot (GRUB) system.  Now, I want to give up Windows altogether (surprise, surprise) and reformat the NTFS partition so Ubuntu can use the space. Can I do this by simply going to System>Administration>Disks>Partitions Tab, selecting the NTFS partition and reformatting it to ext3? If this works, I assume that I would need to mount the new ext3 partition somewhere. I know I could reinstall Ubuntu from scratch and wipe the whole disk clean, but have alot of stuff on the Linux side of the disk that I'd rather not mess with, and was hoping for a simple solution. By the way, my fdisk output is:


Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3465    27832581    7  HPFS/NTFS
/dev/hda2            4886        5005      963900   1c  Hidden W95 FAT32 (LBA)
/dev/hda3   *        3466        4822    10900102+  83  Linux
/dev/hda4            4823        4885      506047+   5  Extended
/dev/hda5            4823        4885      506016   82  Linux swap / Solaris

Partition table entries are not in disk order

thanks in advance

gnuconvert

---

### Post by leech on 2006-01-09
Yeah, that should theoretically work just fine.  You could quite possibly change the mount point to your /home and copy everything from your home directory over to it then reboot.  This will allow you to re-install at a later time without losing all your stuff (if you ever need to re-install for whatever reason.)

Leech

---

### Post by polkadotchickens on 2006-01-11
i'm thinking about doing this too.  would it be possible to invent some directory, say, /spare or something, and have it mount from there?  and then use the partition like just extra space?

---

### Post by gravediggers on 2006-01-11
Yeah, thats probably a better move than shifing /home to there. What you suggested gives you the ideal place to accumulate vast quantities of crap, without overcrowding /home!

---

### Post by Sef on 2006-01-11
What I would do would be like this (assume the hard disk has 100 GB and ram is 512):

system    10 GB   FAT32
root          5 GB   ext3      bootable
home       15 GB  ext3
swap          1 GB  swap

Make your partitions bigger or smaller as you see fit. If you do a lot of downloading, you definitely would want to make it bigger.  And with the extra space, you could leave it until you increase a partition size.

---

