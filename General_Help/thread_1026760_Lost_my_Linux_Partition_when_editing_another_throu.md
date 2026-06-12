---
title: "Lost my Linux Partition when editing another through windows"
date: 2008-12-31
forum: General Help
---

### Post by syle102 on 2008-12-31
Ok, I'm lost here. I have installed ubuntu 8.10 on my computer (upgraded from 8.04) and after the install, I wanted to free up some space on my hard drive, so I went through Windows Vista Business to remove the HP recovery partition, and make it an NTFS partition. 
When I attempted to reboot, GRUB gave me the error: Error 22. 
I'm assuming that this had to do with a reassigning of the partition indices. When I tried to edit the GRUB menu.lst with my ubuntu 8.04 Live CD, I could not mount the linux partition, which is listed as /dev/sda3 when using fdisk -l 

On gparted, the partition is described as unallocated, but it is definitely my linux partition. Is there a way I can fix this, or have I lost my data. Also can I fix grub?

Thanks for the help

ps attached are gparted and fdisk -l screenshots. the unallocated 8.84GB is the HP partition that I wiped, and the unallocated 27.95GB is what I believe is the linux partition.

---

### Post by logos34 on 2008-12-31
> **syle102 said:**
>  I could not mount the linux partition, which is listed as /dev/sda3 when using fdisk -l 

On gparted, the partition is described as unallocated, but it is definitely my linux partition. Is there a way I can fix this, or have I lost my data. 

no, sda3 is the extended partition containing swap and the 'unallocated' space...If / was there it would be named 'sda6'...Not sure what happened here...Was it ok after you installed/upgraded, I mean were you able to boot into 8.10?  

I think the only recourse at this point is to run TestDisk to fix the partition table, or else recover ubuntu / if indeed it somehow got erased.  On the Live CD do:

System>admin>software sources>enable 'Universe' repo

sudo apt-get install testdisk

sudo testdisk

Read [this (6-11)]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_type_selection") and [this (8)]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition")

good luck

---

### Post by syle102 on 2008-12-31
ok I'm running through the testdisk routine. 

The partitions were fine when I updated to 8.10, so that shouldn't be an issue. Must be something that has to do with Windows rewriting partition tables. 

I'll report on testdisk when I get stuck, or finish

---

### Post by syle102 on 2008-12-31
Also is there a way that I can run gparted from the live cd, tell it to make a new partition from the unallocated space ( as an ext3 partition) and then apply the changes without formatting? Would that work to rewrite the index?

---

### Post by logos34 on 2008-12-31
> **syle102 said:**
> Also is there a way that I can run gparted from the live cd, tell it to make a new partition from the unallocated space ( as an ext3 partition) and then apply the changes without formatting? Would that work to rewrite the index?

no, gparted can't do that...only create and format partitions.

(btw, gparted on the ubuntu live cd is listed under system>admin>partition editor

---

### Post by syle102 on 2008-12-31
ok I am in testdisk and confused. 
I have a listing of partitions as given in the attachment.

The highlighted partition is what I believe should have been my linux filesystem. 

I don't understand why I have two linux swap partitions at different locations.


Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
D Linux Swap               0   2  1   242 254 42    3903648
D HPFS - NTFS              0  32 33  3187  45 58   51200000
D HPFS - NTFS           2550   1  1 11006 254 63  135861642
D HPFS - NTFS           3187  45 59  7114 230 28   63098880 [New Volume]
D Linux                 7115   2  1 10762 254 61   58604992
D Linux Swap           10764   0  1 11006 254 44    3903776ndows
D FAT32 LBA            11007   0  1 12029 254 56   16434488 [HP_RECOVERY]
D HPFS - NTFS          11007  15 17 12161   7  6   18538496 [DataNTFS]
D HPFS - NTFS          12030   0  1 12160 254 63    2104515


the 51200000 sector long partition is my windows vista C drive.
The partition listed as 125891642 is listed as NTF found using backup sector! 

[New Volume] is a data partition.
[DataNTFS] was the partition of data that I attempted to create from the HP_RECOVERY partition which is still listed.t is

And there is also a final partition that is 2104515 sectors that I don't know what it is for and why it is listed. 

From this point, I don't know how my system is configured, or how I can fix it. The linux partition is listed as ext3, which is what I want.

Sorry to be so confused, but what does this all mean?
thanks so much

---

### Post by syle102 on 2008-12-31
And also when I go into the advanced tab, as indicated by the data recovery examples tab, I can't find ext3, which is the filesystem I want to restore to, in the list of file systems. Should the previous filesystem be ext3?

---

### Post by logos34 on 2008-12-31
Here's pretty much what you're aiming at:

> D Linux Swap 		0 	 2  1 242 	254 42 3903648
[COLOR="SeaGreen"]* HPFS - NTFS 		0 	32 33 3187 	 45 58 51200000[/COLOR]
D HPFS - NTFS 		2550 	 1  1 11006 	254 63 135861642
[COLOR="SeaGreen"]P HPFS - NTFS 		3187 	45 59 7114 	230 28 63098880 [New Volume]
L Linux 		7115 	 2  1 10762 	254 61 58604992
L Linux Swap 		10764 	 0  1 11006 	254 44 3903776ndows[/COLOR]
D FAT32 LBA 		11007 	 0  1 12029 	254 56 16434488 [HP_RECOVERY]
D HPFS - NTFS 		11007 	15 17 12161 	  7  6 18538496 [DataNTFS]
D HPFS - NTFS 		12030 	 0  1 12160 	254 63 2104515

But the extended partition (sda3) that holds / and /swap isn't showing up.  And there's an overlap between vista and sda2 right at the end [3187]...So do a ['Deeper search']("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Save_the_partition_table_or_search_for_more_partitions.3F")

---

### Post by syle102 on 2008-12-31
testdisk keeps exiting whenever I try to do the second search deeper. When if gives me the list of partitions, I press enter and it exits.

I'm trying one more time

---

### Post by logos34 on 2008-12-31
take a look [here too]("http://www.users.bigpond.net.au/hermanzone/p21.html#Recovering_a_Lost_Partition_With_").

---

