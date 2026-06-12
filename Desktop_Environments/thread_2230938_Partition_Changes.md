---
title: "Partition Changes"
date: 2014-06-22
forum: Desktop Environments
---

### Post by Geoff_Lane on 2014-06-22
Folks,

I've just used dd to clone my laptop's HD  and ended up with a lot more unallocated space.

Obviously I want to use the extra space but I already have 4 primary partitions as follows;

1. Windows Vista (seldom use it). SDA1
2. Vista rescue partition (Never used it). SDA2
3. Linux swap SDA3
4 Ext4 Ubuntu system. SDA4

If I delete the Linux swap then create an extended partition I can recreate the swap there but will my system still boot OK - I am wondering if the existing partitions retain their original partition numbers.

I appreciate I'll have to edit the fstab file for the moved swap but I am more concerned with initial booting.

Geffers

---

### Post by oldfred on 2014-06-22
If willing to edit fstab, it should not be a major issue.

System should boot, but will give some sort of error on not mounting. I would of course always have good backups of Windows and a working live installer to make repairs just in case.

If sda3 & sda4 are next to each other on drive (not a requirement) you can use fixparts to convert them both to logical partitions. I think then the UUID may not change and you do not have to edit fstab.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    
If you do delete it and then recreate swap with new UUID:
       # Find your UUID:
sudo blkid -c /dev/null -o list

   sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

---

