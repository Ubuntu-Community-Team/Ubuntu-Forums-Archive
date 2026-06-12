---
title: "Drive Space Misreported After Upgrading RAID1 to RAID5"
date: 2020-04-07
forum: Desktop Environments
---

### Post by DrewT on 2020-04-07
For some years I had a RAID1 array, assembled under mdadm, consisting of two 2-TB drives. I recently ran out of space and decided to add 2 4-TB drives and upgrade the array to RAID5 with four disks. I encountered many obstacles along the way, but eventually I did manage, through a series of madadm --grow commands, to create the array I wanted. If I had it to do over I would wipe the old drives and create the new array from scratch, but I thought using --grow would take less time than copying all my files over from a backup. I'll know better next time.

The problem now is that the array is not showing up correctly on my system. My file browser, Nemo, shows that the new array still has a total capacity of 2TB. The Disks utility shows a 6-TB array, but identifies it as having the UUID of the old array. Other commands shows similar anomalies:

df -h (as relevant):

[PHP]Filesystem      Size  Used Avail Use% Mounted on
/dev/md126      1.8T  1.7T   31G  99% /media/druid/RAID11[/PHP]

sudo parted -l (as showing the array and its members):

[PHP]Model: Linux Software RAID Array (md)
Disk /dev/md126: 6001GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  6001GB  6001GB  ext4[/PHP]

lsblk (as relevant):

[PHP]sda         8:0    0   1.8T  0 disk  
&#9492;&#9472;sda1      8:1    0   1.8T  0 part  
  &#9492;&#9472;md126   9:126  0   5.5T  0 raid5 /mnt/md-uuid-13131ad9:b01ae9ba:e174a474:ed5fcb2b
sdb         8:16   0   3.7T  0 disk  
&#9492;&#9472;sdb1      8:17   0   1.8T  0 part  
  &#9492;&#9472;md126   9:126  0   5.5T  0 raid5 /mnt/md-uuid-13131ad9:b01ae9ba:e174a474:ed5fcb2b
sdc         8:32   0 465.8G  0 disk  
&#9500;&#9472;sdc1      8:33   0 450.8G  0 part  /
&#9500;&#9472;sdc2      8:34   0     1K  0 part  
&#9492;&#9472;sdc5      8:37   0    15G  0 part  [SWAP]
sdd         8:48   0   1.8T  0 disk  
&#9492;&#9472;sdd1      8:49   0   1.8T  0 part  
  &#9492;&#9472;md126   9:126  0   5.5T  0 raid5 /mnt/md-uuid-13131ad9:b01ae9ba:e174a474:ed5fcb2b
sde         8:64   0   3.7T  0 disk  
&#9492;&#9472;sde1      8:65   0   1.8T  0 part  
  &#9492;&#9472;md126   9:126  0   5.5T  0 raid5 /mnt/md-uuid-13131ad9:b01ae9ba:e174a474:ed5fcb2b
sr0        11:0    1  1024M  0 rom  [/PHP]

I've tried rebooting, unmounting and remounting the md drive, modifying fstab to mount the new drive (by disk-id). I have run out ideas. I can only guess that there's some leftover cruft from the old md drive and that this is somehow messing up with the proper mounting of the new one. I've even wondered if I should just ignore the reported disk capacity and see what happens, but I'd rather clean up whatever mess I've made. All suggestions will be most appreciated.

---

### Post by lvm on 2020-04-08
> **DrewT said:**
> If I had it to do over I would wipe the old drives and create the new array from scratch, but I thought using --grow would take less time than copying all my files over from a backup. I'll know better next time.
Indeed, you have gained valuable experience :) Actually there was an even better way: connect new disks and at least one disk of the old RAID1 array. If you don't have enough SATA connectors use USB cradle or box for the last one. Create a new blank array on new disks and mount old array as degraded and read-only. Now you can copy your data. Or connect 3 new disks and one old, create new degraded RAID5 - it is faster anyway, copy data, then add the last new disk for redundancy - you will definitely have enough connectors this way.

> The problem now is that the array is not showing up correctly on my system. My file browser, Nemo, shows that the new array still has a total capacity of 2TB.
Did you resize the filesystem with resize2fs after resizing the array?

---

### Post by DrewT on 2020-04-08
> **lvm said:**
> Did you resize the filesystem with resize2fs after resizing the array?

Aha! Yes, that seems to have been the missing piece of the puzzle. Thank you! I'm free to love Ubuntu again!

---

