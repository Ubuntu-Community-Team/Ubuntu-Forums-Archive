---
title: "Partition table completely gone"
date: 2010-10-18
forum: Desktop Environments
---

### Post by bgdorazio on 2010-10-18
I Inadvertently deleted a good partition while trying to clean up after a 10.10 update install failure that left grub broken and prevented me from using my working Linux partition.  (installed 10.4 in a new partition)  

Used testdisk to restore the deleted partition which resulted in the entire partition table being wiped out.
All partions are gone, win Xp, 2 Linux partitions, 2 Linux swap partitions.

Testdisk deep search does see the partitions but will not recreate the table.  
Is their anything I am doing wrong in Testdisk that it won't write the table?

Nothing else has been written to the disk.

I very carefully recorded the partition information - is their any way to manually enter?


Any help would be greatly appreciated.

---

### Post by oldfred on 2010-10-19
You can totally use fdisk or sfdisk but I am no expert. 

What does this do. If you see no partitions do not write.

sudo fdisk /dev/sda
x  # enter expert mode
f  # fix  partition table
r  # return
p  # to print
v  # to verify partition 
if ok
w  #  write the changes to disk

---

