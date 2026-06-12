---
title: "How do I defrag my FAT32 Logical (Storage) Partition from my primary Ubuntu?"
date: 2006-04-16
forum: Desktop Environments
---

### Post by braveerudite on 2006-04-16
I have one 160 Gig SATA HDD

I divided the HDD in two (2) Partitions.

Primary Partition 60 Gigs: Ubuntu Linux OS

Secondary Partition 100 Gigs: FAT32 which I'll be using for storage ie , Music, Videos, Documenst...

I created this FAT32 Partition because I'm relatively a noob in Linux and I'm doing lots of experimenting and I mostlikely run the chances of breaking my Ubuntu.  Therefore I created this partition as safety precaution, but there is another problem.   _As time goes by that FAT32 partition is going to get trash slowly, so I need to find a way to drefrag my FAT 32 Partition from Ubuntu every ones in a whiles_

Thank  you

Note: I also created a folder in my home forder called sda5 I did this because when I went to the "Disk Options"  It asked me for an access path for my FAT32 partition, this way I can share and have access to that partition thru my Local home folder and my home network.  

  I access my FAT32 Partition like this:  /home/jok3r/sda5
 Notice that by creating the sda5 folder I can access the FAT32 easy and share it on my home network.  I mention this too because I wonder if this a proper way to access my FAT 32 Partition.  That you all for your time.

---

### Post by babalou on 2006-04-16
[QUOTE=braveerudite]_As time goes by that FAT32 partition is going to get trash slowly, so I need to find a way to drefrag my FAT 32 Partition from Ubuntu every ones in a whiles_
[/QUOTE]
Not sure there is any way to do this from Linux. FAT32 is not a native linux partition (ext3, ReiserFS) which don't have this problem.

just curious about something:
- if you have a windows installation on your machine, you could run the defrag tool from there?
- if you don't, then I don't see why this backup partition has to be FAT32! Why don't you just convert it to a Linux native filesystem which will remove this un-necessary ridicule task? In any case if you system crash, you'll have to repair your Linux partition (then access to your additional partition will always be guaranteed). 
You need FAT32 if you want to run Windows and Linux so that filesystem could be accessed from both OS. So no Windows no FAT needed; if FAT it should imply you have windows on your machine (dual boot).

yb

---

### Post by braveerudite on 2006-04-17
[QUOTE=babalou]Not sure there is any way to do this from Linux. FAT32 is not a native linux partition (ext3, ReiserFS) which don't have this problem.

just curious about something:
- if you have a windows installation on your machine, you could run the defrag tool from there?
- if you don't, then I don't see why this backup partition has to be FAT32! Why don't you just convert it to a Linux native filesystem which will remove this un-necessary ridicule task? In any case if you system crash, you'll have to repair your Linux partition (then access to your additional partition will always be guaranteed). 
You need FAT32 if you want to run Windows and Linux so that filesystem could be accessed from both OS. So no Windows no FAT needed; if FAT it should imply you have windows on your machine (dual boot).

yb[/QUOTE]


I have to separate machines... 

I undertand the fact that Windows can't read Linux partitions but if I make the backup partition ext3, can windows read it thru a Network and access files from it. ie.  Share the back up ext3 Linux partition on a network and get files from it using my windows box?

---

### Post by unbuntu on 2006-04-17
[QUOTE=braveerudite]I have to separate machines... 

I undertand the fact that Windows can't read Linux partitions but if I make the backup partition ext3, can windows read it thru a Network and access files from it. ie.  Share the back up ext3 Linux partition on a network and get files from it using my windows box?[/QUOTE]

Maybe not pertaining to the topic, but just for your information, you can mount ext2/3 file systems under Windows through these tool introduced here:

[http://kennethhunt.com/archives/001314.html](http://kennethhunt.com/archives/001314.html)

---

### Post by babalou on 2006-04-17
[QUOTE=braveerudite]I undertand the fact that Windows can't read Linux partitions but if I make the backup partition ext3, can windows read it thru a Network and access files from it. ie. Share the back up ext3 Linux partition on a network and get files from it using my windows box?[/QUOTE]
If your intent is to network share your files only, then running **Samba **on your linux box is what you need. All your samba share will be available from any box (Win, Linux,..) from your network in read/write mode! This disregarding the filesystem used on your Linux box: so switching from FAT32 to a more robust/efficient filesystem (reiserfs, ext3,...) and installing **Samba **might be a good idea :-k 

yb

---

### Post by Ramses de Norre on 2006-04-17
If you enter a linux computer through a network it's the linux computer who is reading/writting to his own filesystems on demand of the computer you browse it from. So it doesn't matter which OS is running on the computers, you only need the right protocol (and all popular OS's have smb).

---

