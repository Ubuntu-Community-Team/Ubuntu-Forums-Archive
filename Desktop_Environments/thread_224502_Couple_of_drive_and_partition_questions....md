---
title: "Couple of drive and partition questions..."
date: 2006-07-28
forum: Desktop Environments
---

### Post by petersjm on 2006-07-28
Hi guys,

Thanks to [Peturr's](http://www.ubuntuforums.org/member.php?u=48310) excellent HowTo on [getting WinXP to run in VMWare on Ubuntu](http://www.ubuntuforums.org/showthread.php?t=183209), I have now got it up and running and want to delete the Windows partition on my HDD. In gParted, FAT32 and NTFS partitions are listed first (i.e. before ext3 etc). So, I have a couple of questions I hope some kind person would answer:

1. If I format the FAT32 and NTFS partitions, will it have any effect on the WinXP installed as a virtual machine through Ubuntu?

2. Can I reformat the partition(s) as an additional ext3 partition to use as extra storage space and "take back" half my drive space? (i.e. can I have two ext3 partitions without problems?)

3. If I do reformat to ext3 (or whatever), will I have to do anything to grub to remove the WinXP boot option? Or will it automatically remove WinXP from the list itself?

And finally, on another point:

4a. I'm thinking of buying an external hard-drive for additional storage (I've only got a 40Gb drive and it's quickly filling up!) I've found a 160Gb USB-connected drive that's relatively inexpensive, but I'd like to know if there's anything I need to do when I buy it, other than plug it in and boot up? (like format, partition, etc)

4b. I'm assuming it'll appear on my desktop just like any other USB device when it's plugged in. But can I add it to fstab to enable auto-load of the drive (and therefore keep the drive plugged in at all times)? Or do I even need to?

Questions, questions... Sorry! Hope someone can help :D

---

### Post by OpsVentus on 2006-07-28
1 This depends on where you installed Windows during the vmware install:
Insert your Windows (XP) CD into your CDROM drive
Open the VMware Server Console
select 'Create a new virtual machine'
=> Next => Next => Select Windows Xp (or whatever Windows versions you want to install )
=> Next => Enter a name and select a location for the Virtual Machine File (It contains the virtual harddisk, so it needs quite some space, min 2 GB, but I would recommend 8+ GB )
=> Next => Select Network type. I am using NAT, but choose whatever fits you ( or your mood )
=> Next => Choose the size for the Virtual Disk and set other preferences
=> Next => Finish

If it isn't on those partitions and there's nothing other you want to keep on there, you can remove it.

2 Then you can format them to ext3 and take back half your drive space. ;)

3 Grub will not see by it self Windows is removed, but this is easy. Open Grub's menu.lst(sudo gedit /boot/grub/menu.lst) and put an '#' in front of every line in the Windows part.
Post the file here if you want me to show you exactly where.

4a Most external drives will be formatted when you buy then. The question is if you want it to be fat32(or how it's formatted).
I formatted mine to ext3. And if you want more partitions, then you have to partition it.
This is a small problem, look at the drive first.

4b You do not need to put 'm in your fstab, but you can if you want.
I didn't, it mounts the way I like it by default.
Another small problem, look at the way it mounts first.

Cheers,
Bart.

---

### Post by petersjm on 2006-07-28
Thanks Bart. Much appreciated. I'll post Grub's menu.lst if I need to. Thanks again.

---

