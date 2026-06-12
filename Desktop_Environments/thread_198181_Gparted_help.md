---
title: "Gparted help"
date: 2006-06-16
forum: Desktop Environments
---

### Post by LopsidedElf on 2006-06-16
Hi i have a 250 gig hard drive divided up into two partitions a 20 gig one in ext3 that i think is / and /home and on the 230 gig is the swap. This is due to a newb install on my part and i was wondering if there was anyway to fix this using the whole drive for ubuntu. Also i was wondering what was the best way to set up my partitions. Thanks.

Alternatively, is there anyway i can save my whole configuration of this install onto a fresh one so it will work the same way this one does? Thanks for any help.

---

### Post by Herman on 2006-06-16
Hello, LopsidedElf, the best and easiest way is to download a [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and burn it to a CD-RW or CD-ROM disk. It's less than 30.0 Mb to download and it's almost the same as the GParted on the Ubuntu 'Desktop' Live/Install CD, but it might be better. You won't have to worry about unmounting your partitions with GParted LiveCD because it mounts them automatically as 'fakeraid'.

Linux partitions can be copied and pasted and they can be resized from the end of the partition but not from the beginning. The beginning or start of a Linux filesystem is fixed, so Linux partitions can't be 'moved' like partitions with other types of filesystems can.
If you need to copy and paste your partitions around, shrink them first so you'll have lots of room.
Each time you copy and paste them, you will notice they get a new partition number. You need to end up with the same partition numbers as you started with. That means you might need to copy the partition and paste it somewhere out of the way and delete the original one. Then copy new one and paste it where you really wanted it and it should get the  old partition number back like it had before, but be where you need it.
If you don't feel like doing that, (double copying and pasting to preserve the partition numbers), you can just copy and paste once and then edit /etc/fstab instead, with the new partition numbers, and then your system will work properly again.
```
250 gig hard drive divided up into two partitions a 20 gig one in ext3 that i think is / and /home and on the 230 gig is the swap.
```I don't understand what you mean here? :confused: But if you want specific help, paste a copy of the output of sudo fdisk -lu and I'll know what you want better then. ```
sudo fdisk -lu
``` :D Regards, Herman :D

---

### Post by LopsidedElf on 2006-06-16
Hey thanks for your help im still pretty confused though since im a rather newb with linux heres my fdisc -lu output:

> Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1        40162500   488375999   224106750    f  W95 Ext'd (LBA)
/dev/hda2   *          63    40162499    20081218+  83  Linux
/dev/hda5        41945778   488375999   223215111    e  W95 FAT16 (LBA)
/dev/hda6        40162626    41945714      891544+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      224909      112423+   0  Empty
/dev/sda2          224910   117210239    58492665    b  W95 FAT32


---

### Post by Herman on 2006-06-17
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

Device.....Boot.........Start.......End..............Blocks........Id..........System

/dev/hda2...*.............. 63....40162499....20081218+......83....Linux..........20.0.GB.[Ubuntu,ext3?]
/dev/hda1.......40162500...488375999...224106750... f W95....Ext'd.(LBA)
/dev/hda6.......40162626....41945714......891544+......82....Linux swap / Solaris.0.912.GB[Swap]
/dev/hda5.......41945778...488375999...223215111.e....W95....FAT16.(LBA)..........228.0.GB.[data ?]

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

Device.....Boot...Start.......End.........Blocks......Id......System
/dev/sda1............63......224909.......112423+......0......Empty
/dev/sda2........224910....17210239......58492665...b.W95.....FAT32

>  Hi i have a 250 gig hard drive divided up into two partitions a 20 gig one in ext3 that i think is / and /home and on the 230 gig is the swap. This is due to a newb install on my part and i was wondering if there was anyway to fix this using the whole drive for ubuntu. Also i was wondering what was the best way to set up my partitions. Thanks.

Alternatively, is there anyway i can save my whole configuration of this install onto a fresh one so it will work the same way this one does? Thanks for any help. LopsidedElf, I re-arranged your fisk output into disk order and did some rough calculations for you. It looks like you probably have Ubuntu installed with just one nice 20.0 GB single partition '/' install and a 1.0 GB swap area. That's a very good partitioning scheme already. You want to make it bigger, eh?

Okay, well first we should check and make sure there's no data on the 230.0 GB FAT16 partition that you care about. Are you sure about that or would you like some help to try and mount it so you can have a look first to make sure? We wouldn't want to delete anything important to anybody. You may have an icon on your desktop for it already, or a directory in /media that you can open to look at it. Otherwise, let me know and we'll make one and mount your partition in it.

If you are sure there's nothing there you care about, just start your GParted LiveCD and select that partition and delete it and click apply and then wait a few minutes. 
When that's done you can click on the swap area and move it to the end of your disk. Click apply again.
Shrink the extended partition (box that the swap are will be in), to the size of the swap area.
After that, just click your Ubuntu partition and resize it, it should be easy.

---

### Post by LopsidedElf on 2006-06-18
Thanks for all the help its much appreciated

---

