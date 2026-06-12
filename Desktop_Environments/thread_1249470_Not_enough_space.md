---
title: "Not enough space"
date: 2009-08-25
forum: Desktop Environments
---

### Post by Trancas on 2009-08-25
Hello,

I'm very new in the Linux/Ubuntu world. I just installed Ubuntu 9.04 in my laptop (Lg R200). I installed Ubuntu in one partition and in another partition I install Vista. But I think I have a problem with the partition were I put Ubuntu, because every time I try to update in the Update Manager I have this error message: "The upgrade needs a total of 392M free space on disk '/'. Please free at least an additional 342M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'." I tried to do this, but it didn't work...

Can anyone help me...

Thanks

---

### Post by abelta on 2009-08-25
Looks like you assigned very little space to your Ubuntu partition and you should either free some space or reassign the space for each partition.
The second option is more complicated and involves creating a live CD for GParted (wich I haven't been able to do in the past for the life of me) so your best option should be to erase some movies or games.

---

### Post by slakkie on 2009-08-25
Please check the pointers from this thread:

[http://ubuntuforums.org/showthread.php?p=7775158](http://ubuntuforums.org/showthread.php?p=7775158)

---

### Post by Trancas on 2009-08-25
Thanks for the quick reply!

But I put enough space in both partitions. Partition for Vista: 50GB; Partition in Ubuntu: 100GB. And I just clean my laptop and install Vista and Ubuntu, I don't yet put nothing in my laptop...I don't know if it helps, but in my Place I have three disk drives: One call SYSTEM, where I put Vista with 50GB, and it have 25.7 GB of free space. Another one call BACKUP, where I put Ubuntu and it have 95.5 GB free and 88.6 MB used. And a last one call WINRE with 1GB, 302.3 MB free space and 721.7 MB used.

---

### Post by goseph on 2009-08-25
> **abelta said:**
> 
The second option is more complicated and involves creating a live CD for GParted (wich I haven't been able to do in the past for the life of me) 
 
Creating a live CD with GParted is very easy, gparted comes with ubuntu as standard.
 
Download a .iso of the latest Ubuntu.
 
Burn it to a spare CD
 
Boot from the CD
 
type "sudo gparted"
 
and you're laughing!

---

### Post by scrooge_74 on 2009-08-25
in terminal type df to see how mouh space you have, also type mount and show but results.

Maybe your partition scheme left something unmounted or your /home partition is too small

---

### Post by mcduck on 2009-08-25
> **Trancas said:**
> Thanks for the quick reply!

But I put enough space in both partitions. Partition for Vista: 50GB; Partition in Ubuntu: 100GB. And I just clean my laptop and install Vista and Ubuntu, I don't yet put nothing in my laptop...I don't know if it helps, but in my Place I have three disk drives: One call SYSTEM, where I put Vista with 50GB, and it have 25.7 GB of free space. Another one call BACKUP, where I put Ubuntu and it have 95.5 GB free and 88.6 MB used. And a last one call WINRE with 1GB, 302.3 MB free space and 721.7 MB used.

OSunds like something went wrong when you were partitioning, or you made a mistake.

You Ubuntu root partition definitely will not show under hte Places-menu with any name like "BACKUP" or anyhting.

How did you do the partitioning? Did you use Ubutnu's partitioner or did you create the partitions with some orther tool beforehands? Pehaps you didi a FAT or NTFS partitions for Ubuntu beforehands, and then the insaller resized that partition and made a small root partition for Ubutnu inside it?

Could you open a terminal (Applications/Accessories/Terminal) and run following commands? Post the outputs here..
```
sudo fdisk -l
df -h
```
(the first one will list all your disks, and partitions in them, and the second one tells the amount of free space on each partition.)

---

