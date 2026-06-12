---
title: "External USB Drive"
date: 2005-12-10
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-10
My goal : to do a backup of my Ubuntu Breezy to a partition on an external USB drive. 

If I go to computer I can see the drives and view the contents. When I do fdisk -l they are listed also. Two of the partitions are NTFS for my windows backup. Two of the partitions are ext3 for linux backup.
When I go into /dev all the drives are listed in yellow in a black backround.
None of the partitions are listed in fstab.
I tried to chmod a+rwx sda5 and sda6 (other linux partition. It seemed to work but nothing changed.

The problem: first I can not add anything to the drives. Second I can not figure out how to get to the drives from the command line. /cd/sda5 wont work as it is not a directory. 
If I could figure out how to access the drives maybe I could do a backup to the partition. 

It is a 200g drive 4 partitions.
  
Any suggestions?

Charlie

---

### Post by CharlieC on 2005-12-10
Addition to previous post. 
sda5 shows up when I do cd /. It shows as any other directory. I can swithch to it but still can not copy a file to it. I did check the permission and I am supposed to be able to read, write and execute as root.

Charlie

---

