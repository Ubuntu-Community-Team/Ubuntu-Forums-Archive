---
title: "Resizing Windows and Linux Partitions"
date: 2005-12-23
forum: Desktop Environments
---

### Post by zappa86 on 2005-12-23
I installed linux on my friends laptop a few days ago. He has an 80gb harddrive and during the install re resized it down to 65 and gave 15 to linux. Now hes lovin' linux so much he wants to make it even bigger and windows even smaller. We downloaded gparted, however we cant seem to make it work. Does anyone know who to resize an NTFS and then resize and ext3? Thanks.

---

### Post by dcstar on 2005-12-23
[QUOTE=zappa86]I installed linux on my friends laptop a few days ago. He has an 80gb harddrive and during the install re resized it down to 65 and gave 15 to linux. Now hes lovin' linux so much he wants to make it even bigger and windows even smaller. We downloaded gparted, however we cant seem to make it work. Does anyone know who to resize an NTFS and then resize and ext3? Thanks.[/QUOTE]
Probably better to resize the NTFS partition with a Windows utility, and once that is done use gparted - or "parted" in a recovery boot-up - to do the rest.

I recall resizing a FAT32 partition ok, but I don't know how well NTFS ones will go.

---

### Post by briancurtin on 2005-12-23
the reason parted/gparted might not be working is because you cant do this work while the drive is mounted. you will have to run this from a recovery boot up, or it can be done easily from a live CD like the ubuntu one.

also, if the windows drive has anything in it, defragment the drive before you do this so that the data is moved closer together in the beginning of the partition. since it sounds like this is pretty fresh, you might not have to worry about it, but with windows you never know what the hell they did.

---

### Post by anil_robo on 2005-12-23
[quote=briancurtin]the reason parted/gparted might not be working is because you cant do this work while the drive is mounted. you will have to run this from a recovery boot up, or it can be done easily from a live CD like the ubuntu one.[/quote]
I guess it's the INSTALL CD that has the partitioner/resizer, not the live CD. :)

> also, if the windows drive has anything in it, defragment the drive before you do this so that the data is moved closer together in the beginning of the partition. since it sounds like this is pretty fresh, you might not have to worry about it, but with windows you never know what the hell they did.

I tried resizing my windows partition yesterday, and lost everything! I did not defragment though, and I don't remember correctly if it was an NTFS partition! However, I successfully backed up all data on my webspace!

---

### Post by exclipy on 2005-12-25
Is it possible to resize ext3 filesystems these days (mounted or not)?  parted tells me "the ext2 filesystem has a strange layout" and resize isn't supported yet.

---

### Post by foolosophy on 2005-12-26
It is possible, I've done it.


First, you need a live CD, I suggest Knoppix. If you have the Ubuntu Install CD you can boot that, and then after all the hardware detection, when you get to the partitioning stage, press CTRL-ALT-F2, and with the console you can run "parted" I believe. But I'm almost sure that it doesn't support NTFS resize: Knoppix does.

If you can, backup your data just in case.

It would be advisable to defrag the NTFS partition. Once you do this, you can boot with the live CD and resize the ntfs partition with
```
sudo parted /dev/hda
``` there use the command "print" to checkout the layout of your drive. 

I assume that your disk is

hda1: ntfs
hda2: extended
hda5: /boot
hda6: /
hda7: swap

to shrink NTFS use the command "resize". 

If you want to make your "/" partition bigger but you have "/boot" partition first, you'll probably need to delete that partition and move it to the end of your "/" partition. You may do this shrinking a little bit your "/" and then moving the boot partition to that free space with the command "move" in parted.

And as ext3 resize is NOT SUPPORTED, you can transform your ext3 partitions into ext2, resize them with parted, and then turn them back into ext3. The commands are the following (I learnt this from Herman [http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted]("http://www.hermann-uwe.de/blog/resizing-ext3-partitions-with-parted"))

Remove the ext3 journal from hda6 (effectively turning it into an ext2 partition):
# tune2fs -O^has_journal /dev/hda6

Resize with parted

Enable the ext3 journal again on the now enlarged hda6:

# tune2fs -j /dev/hda6


That may solve your problem. I suggest you make a backup especially of your "boot" partition, because I had problems booting when I did it, because I did it unappropiately.


A very useful tool I discovered today is "gpart". Google for that, you can run it from a floppy once you load any command-line linux. This tool recognizes your partitions even when you messed up the partition tables.

---

### Post by briancurtin on 2005-12-26
[QUOTE=anil_robo]I guess it's the INSTALL CD that has the partitioner/resizer, not the live CD. :)[/QUOTE]
i ran gparted from the ubuntu live CD. the install CD has a partitioner as well.

---

