---
title: "What is the best partitioning scheme?"
date: 2006-01-10
forum: General Help
---

### Post by inigmatus on 2006-01-10
Hi, I'm totally new to Linux and the various filesystems it can use.

I have a 100GB drive that holds and runs my XP. I don't want it touched.

I have a 2nd drive that is 42GB that I would like to have XP and Ubuntu to share.

I have a 3rd drive that is 20GB that I would like to install Ubuntu to.

I have a Knoppix Live CD and a Ubuntu Live CD I can boot from to get started. I plan to use qtparted to partition the drives, and then use the Ubuntu Installer CD to create a place for me to play on in this brave new world.

Does anyone have any suggestions on how best to partition my drives for the optimal experience? 

What is the difference between reiserfs and ext2 and ext3? Is it necessary to know the difference when starting out in the Linux world?

---

### Post by Qrk on 2006-01-10
Don't touch the first drive except for MBR (and only do that if Ubuntu claims to have detected windows in the the install, don't worry you will be prompted after partitioning, before ejecting the cd)

The 42 GB drive should be FAT 32, as both Linux and Windows can read/write it. It could also be ext3 if you want to download a third party windows app.

The third can be partitioned many ways. You will need 2 times your RAM in swap and a partition for the / directory. This would work:

hdc1 (or whatever Ubuntu calls the drive) /              19 GB    ext3
hdc2                                                                  1 GB     swap (automatic)

or if you want to be able to reinstall while keeping your home directory.

hdc1      /           9 GB    ext3
hdc2      /home    10GB   ext3
hdc3      swap      1 GB   swap

---

### Post by healychan on 2006-01-10
> I have a 2nd drive that is 42GB that I would like to have XP and Ubuntu to share.

If you format this hard disk to NTFS, Ubuntu will be able to read but not write. Therefore, if you think you will need to write to it on Ubuntu, you should use FAT instead.

> I have a Knoppix Live CD and a Ubuntu Live CD I can boot from to get started. I plan to use qtparted to partition the drives, and then use the Ubuntu Installer CD to create a place for me to play on in this brave new world.

Does anyone have any suggestions on how best to partition my drives for the optimal experience? 
The installer of Ubuntu will guide you to do the partitioning. There are normal partition and partition with LVM, which is something more advance. But anyway, the installer will provide you all the information you need.

> What is the difference between reiserfs and ext2 and ext3? Is it necessary to know the difference when starting out in the Linux world?
You don't really need to know the different between them.

---

### Post by zoiks on 2006-01-10
2nd drive -> Split into 2 fat32 partitions.  Both linux and xp can read/write fat32, but I believe fat32 partitions are limited to 32GB.

3rd drive -> 19G for ubuntu, ~1G at the end for swap.  I'd recommend either ext3 or reiserfs.  From a user perspective, I think ext3 and reiserfs are very similar, and both seem very stable.

You might be better off switching drives 2 and 3, so you can have full 40G for ubuntu and needing only 1 partition for the fat32 shared drive.  JMHO

---

### Post by healychan on 2006-01-10
[QUOTE=Qrk]
The third can be partitioned many ways. You will need 2 times your RAM in swap and a partition for the / directory. This would work:

hdc1 (or whatever Ubuntu calls the drive) /              19 GB    ext3
hdc2                                                                  1 GB     swap (automatic)

or if you want to be able to reinstall while keeping your home directory.

hdc1      /           9 GB    ext3
hdc2      /home    10GB   ext3
hdc3      swap      1 GB   swap[/QUOTE]
You don't need that much space for swap. Today's computer used to have more than 64MB. Swap area will be used when running out of physical RAM. I really don't suggest you spare 1GB for swap because it is kind of waste.

---

### Post by inigmatus on 2006-01-10
Thanks for all the input so far. Once I get this straightened out with you guys (man you all are great!), I'm headed for Ubuntu. 

I have 1 GB RAM on my machine. Would a 2GB swap be recommended or needed then? 

Also, I know the 42GB drive will need to be FAT32 to be seen by both OSes, but can XP mount a FAT32 partition greater than 32GB, or is that just the WinXP format limit? I tried a test format to FAT32 for the full 42GB using qtparted last night, but I could not get it to mount in XP. If anyone has a link to help me mount a FAT32 partition greater than 32GB in XP, would be appreciated. The reason I need the 42GB to share between XP and Ubuntu is primarily for sharing reasons - I have a lot of (legal) disk images I like to share, and free music and videos. I don't mind splitting it into two partitions if thats the only way I'm going to get that drive to show up on both systems. 

Knowing that I have 1 GB RAM, how then would you recommend partitioning my 20GB drive for Ubuntu? Should I use ext3 for all partitions on this drive or reiserfs?

---

### Post by healychan on 2006-01-10
> I have 1 GB RAM on my machine. Would a 2GB swap be recommended or needed then? For normal usage, you don't need 2GB swap, not even 1MB. But I suggest you spare 128-256MB just in case.

> Also, I know the 42GB drive will need to be FAT32 to be seen by both OSes, but can XP mount a FAT32 partition greater than 32GB, or is that just the WinXP format limit?I heard that people can have more than 32GB on FAT32 partition. Sorry I couldn't remember the details but surely you can have 42GB partition with FAT format. Try to search this forum and I am sure it is somewhere.

> Knowing that I have 1 GB RAM, how then would you recommend partitioning my 20GB drive for Ubuntu? Should I use ext3 for all partitions on this drive or reiserfs?
If this partition is for Ubuntu only, use ext3 will be OK. The number of partition depends on how you are going to organise you disk space, I can't help with this, you have to make you decision. As I mention before, 128-256MB swap will be more than enough.
I also suggest you do the partition with the Ubuntu installer. And choose to use LVM. Using LVM will allow you to change the size of partition without affecting the data. A more flexible approch if you don't know much about filesystem.

---

### Post by inigmatus on 2006-01-11
Thanks for the replies. I am posting this from my first Ubuntu install!

I have a 1GB swap, 8GB ext3 root, and 9GB ext3 home. Is there a way I can resize my swap partition to 512MB and move the other 512MB to my 9GB home partition without screwing anything up in the process? Or would it be better for me to start completely over with the new partioning scheme?

I want a 512MG swap if I don't need 1GB. With a 20GB drive, every MB matters.

---

### Post by eqisow on 2006-01-11
Yes, you should be able to resize your swap and move the free 512 MB, however it would probably be better just to kill everything if you haven't already installed. Also, I've never run into the problem with limited FAT32 partition size. I have an 80GB storage drive that I keep FAT32 and Windows XP as well as Ubuntu read it just fine. I don't really recall, but I think I used Ubuntu's paritioner to format it as FAT... or maybe I was using Suse at the time. Either way, it shouldn't really matter.

Edit: Windows recognized my 80GB FAT drive automatically, I didn't have to do anything.

---

### Post by healychan on 2006-01-11
[QUOTE=inigmatus]Is there a way I can resize my swap partition to 512MB and move the other 512MB to my 9GB home partition without screwing anything up in the process? [/QUOTE]
You can resize the partition without affecting the data if you do partitioning with LVM.
I don't know if you can do the same with normal partitioning.

---

### Post by inigmatus on 2006-01-11
Ok. I'll just repartition then under LVM and start over. Besides, I'll gain more experience this second time around.

I got my FAT32 42GB drive to mount in XP just fine.  Now that I know how to set this up, my final look will be:

100GB NTFS Windows XP drive (untouched)
42GB FAT32 drive (for hoarding and sharing massive amounts of downloaded files)
20GB drive for Ubuntu partitioned as:
[LIST]
[*]512MB Swap
[*]8GB ext3 /
[*]9GB ext3 /home
[/LIST]

Thanks for the help guys. You've planted a newbie seed into the ground and watered it well. Let's see what happens!

---

### Post by Sef on 2006-01-12
> What is the difference between reiserfs and ext2 and ext3? Is it necessary to know the difference when starting out in the Linux world?

ext3 is an updated version of ext2.  Reiserf and ext3 are just ways to format a partition.   Basically they are the same with one exception.  If you keep adding to a document, e.g., writing a book or a disertation, you could start to fragment in ext3 because it sets aside a certain amount of room.  If you go beyond that amount it will place the other parts on another section of the hard disk.   With Reiserf, it will just add on more room, so it doesn't run the risk of fragmenting.  So unless you are planning on writing a document that will be continuously added to there really isn't any difference for the average user.

---

### Post by will103 on 2006-01-12
[QUOTE=healychan]You can resize the partition without affecting the data if you do partitioning with LVM.
I don't know if you can do the same with normal partitioning.[/QUOTE]

You can do it with normal partitioning as well. 

Try booting your machine using either Knoppix or Kanotix. Both of these live distros have QTParted installed. This app can resise partitions. If you are using a journaled file system such as Reiser or Ext3 then next time you reboot, the system will probably complain that the journal records are inconsistent with the new partition table. However this is not such an issue as you can reset the journaling - I cannot remember how to do this. Can anyone else remember?

As ever - I would make sure that you back up everything first before attemting to resize partitions.

Best of luck

Will103

---

### Post by inigmatus on 2006-01-12
I wonder if documentation for any of this is found on the ubuntu wiki. I haven't seen much info about partitioning there so far.

---

