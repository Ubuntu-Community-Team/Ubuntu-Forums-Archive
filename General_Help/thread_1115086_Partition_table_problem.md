---
title: "Partition table problem"
date: 2009-04-03
forum: General Help
---

### Post by Chikitulfo on 2009-04-03
Hi all,

I have a problem with my ubuntu partition.
I have a 500gb Hd with windows xp(20gb aprox), Ubuntu 8.10 (10gb), swap(2gb) and a data partition (NTFs 160Gb) and some space unpartitioned.

So a week ago I thought that I could make bigger the data partition, but when I opened gparted it told me something like "Error: can't have overlapping partitions" and showed all my Hd in blank to make partitions on it.
Which didn't make any sense to me (I was using all my partitions without any problem).
I searched how to solve it and found testdisk( Which was supposed to restore my partition table back to normal).
So yesterday I ran it and analysed my hard drive to restore my partition table. I was working on ubuntu and everything went fine.
I turned my computer off normally and then, when I turn it on this morning, Bam! Grub error 17 (or 18, not sure).
SuperGrubDisk won't restore grub(although it allows me to run XP) and if i try from a live cd, it lets me mount de Xp and Data partitions, but won't let me mount the ubuntu partition.

the mount command says:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


The thing is that i have very important data in my ubuntu partition and i need to recover it.
So if you could help me to re-access ubuntu...

Thank you very much.

---

### Post by meierfra. on 2009-04-03
> but when I opened gparted it told me something like "Error: can't have overlapping partitions" and showed all my Hd in blank to make partitions on it.
Which didn't make any sense to me (I was using all my partitions without any problem).

 Gparted is pretty picky. If a partition table does not follow all the formal rules of a partition table, gparted will show the whole drive as unallocated, even if you don't have any problems with your partitions.

Anyway, it seems something went wrong when you fixed the partition table with testdisk.  But there is a good chance that testdisk will be able to fix the problems it caused.

So  boot from your Live CD, download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static  /dev/sda

```
(here /dev/sda needs to be replaced by the device name of your Ubuntu drive. It probably is "/dev/sda" but you should check with "sudo fdisk  -lu")

After starting testdisk with the above command, choose
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" (to search for Vista partitions)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.


In addition, post the output of

```
sudo fdisk -lu
sudo sfdisk -d
```

---

### Post by Chikitulfo on 2009-04-04
Thank you Very Much!!
I managed to solve it.
The problem was that I didn't make a deep search the first time 
(because i thought testdisk madeit itself).
So now when i did it, it showed this:
[IMG]http://img14.imageshack.us/img14/1465/terminalh.png[/IMG]
The second linux line was the good one, (I could see all my data by pressing "p"). And testdisk the first time put the first linux line as the good one(they only differ in the head, 0 and 2)
So I changed the second linux line to primary and the linux swap (was also marked as deleted) to logic.
I wrote it on the disk, and Everything was fine.
restored the Grub with superGrubDisc and grub loads again with no problems.
Only that in /boot/grub/menu.lst I had to change the lines:
	root		(hd0,5)
to:
	root		(hd0,1)

Thank you very much!!

---

### Post by meierfra. on 2009-04-04
> I managed to solve it.

Great. Have fun with XP and Ubuntu.

---

