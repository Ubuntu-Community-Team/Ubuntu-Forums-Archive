---
title: "NTFS/FAT32 partitioning help"
date: 2006-01-01
forum: General Help
---

### Post by canadianwriterman on 2006-01-01
I want to create a small FAT32 partition on my master HD, on the same HD as Windows XP. Ubuntu is on my slave HD.

The master HD is 40 Gb. I used gparted (installed from Synaptic) to resize the NTFS partition to 30 Gb. It appeared to work. However, when I rebooted into Windows XP, the NTFS partition still shows at 40 Gb. When I reboot into Ubuntu and check gparted, it also shows the NTFS partition at 40 Gb.

Once I get the NTFS partition downsized. Then I want to create a FAT32 partition on the same HD. If anyone can help me with the resizing step, I'll come back for help on the creation of the FAT32 partition.

Thanks a million.

---

### Post by Luke771 on 2006-01-01
I dont really know that much about this but I have heard many times that you should not use Linux to do anything but reading NTFS partitions.
My advice is to use a Partition Magic bootable CD, it is available in stores at a fairly obscene price, There are also free alternatives on the Internet (BitTorrent), then you can burn it on CD using Nero in Windows or something that does the same tricks in Linux; I'm pretty sure that there is plenty of ISO image-burning Linux software out there.If you decide to use Windows and Nero, you don't even need the whole Nero suite, which is basically one good 35 meg CD-DVD burning utility, plus hundreds of megs of useless crap. Nero 7 basic will do.
Anyways, you must burn the image (not just copy the file on CD) for your CD to be bootable; in Nero you select "burn image" from the Recorder menu and browse to the location of your ISO, then hit "Burn".
Now you got a bootable Partition Magic CD, with intuitive GUI and everything you need to make, delete, resize, convert and set active partitions, with support for both Linux-like and Windows-like file systems.
I have partitioned my (only one and only 40 gig) hard drive to have the two primary partitions NTFS and Ext3 big enough to hold the OS's and a couple of gig of free space to install more programs on each partition, then:
one 6gig NTFS primary Windows OS par.
one 5,5 gig Ext3 Ubuntu OS par.
one logical Linux 2,2 gig Linux swap par.
one logical 2,0 NTFS partition where I installed the 1650MB fixed-size Windows page file.
All the remaining free space is  formatted as logical FAT32, accessible by both OS's for file storage.
I really dont understand why most people make a big partition for each OS and a small FAT32 to exchange files between OS's, when you can store files on a big FAT32 accessible by both (I call it the Big Fat partition) and use the two OS partitions only to install programs.
(maybe I shoud post my partition settings as an how-to, but first I want to hear what some more experienced Linux user have to say)

---

### Post by Omnios on 2006-01-01
I did something similar here is a thread on what I did

[http://ubuntuforums.org/showthread.php?t=45605]("http://ubuntuforums.org/showthread.php?t=45605")

 Note you need the ntfs plug in for Qt parted to resise and found that I tryed with out the plug in and it seemed to work but didn't.

 Also I think the ntfs drive has to be unmounted to resise and partition it.

---

### Post by canadianwriterman on 2006-01-01
[QUOTE=Omnios]I did something similar here is a thread on what I did

[http://ubuntuforums.org/showthread.php?t=45605]("http://ubuntuforums.org/showthread.php?t=45605")

 Note you need the ntfs plug in for Qt parted to resise and found that I tryed with out the plug in and it seemed to work but didn't.

 Also I think the ntfs drive has to be unmounted to resise and partition it.[/QUOTE]

Greetings fellow Ontarian, and Happy New Year. Thanks for the information. I switched from gparted (which didn't work) to qtparted (which worked beautifully). Qtparted resized the NTFS partition and created a new FAT32 partition very smoothly, although it didn't tell me to unmount the partition before doing the work, like gparted did.

I added a line to my fstab file and everything works like a charm. Thank you!

---

### Post by iand675@gmail.com on 2006-01-01
the windows program from the acronis company is an amazing partition and boot managing program. But I wouldn't install the boot manager just in case. Ahem... *I do not suggest looking for a torrent for that program on pirate bay* *I do not condone the illegal downloading stuff* *but you can*

---

### Post by iand675@gmail.com on 2006-01-01
beat me to a solution.

---

