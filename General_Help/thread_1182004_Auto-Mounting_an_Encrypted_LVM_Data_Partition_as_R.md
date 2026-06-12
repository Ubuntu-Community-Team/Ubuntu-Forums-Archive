---
title: "Auto-Mounting an Encrypted LVM Data Partition as Read-Write by Any User"
date: 2009-06-08
forum: General Help
---

### Post by maeyhem on 2009-06-08
I managed to make great use of the encryption+LVM features when installing Jaunty from the alternate cd. My 500 GB HD is configured as follows:
   
  /sda1 ext3 /boot 0.2 GB
  /sda2 ext3 swap 1 GB (encrypted with a random key)
  /sda3 LVM (encrypted with password)
  LVM:
       V1 root ext3 /              10 GB
       V2 data ext3 &quot;mount point&quot;  489 GB
   
  What I'm having difficulty with is selecting a &quot;mount point&quot; and fstab configuration such that V2 shows up under MyComptuter and is read-write accessible by any user. When I use /mnt/Data, the partition is not visible/accessible. When I use /media/Data, the partition is visible, but read-only. 
   
  Opening up /etc/fstab, I saw the entry 
   
  /dev/mapper/data /media/Data ext3 relatime 0 2
   
  which I changed to
   
  /dev/mapper/data /media/Data ext3 auto,users,rw,relatime 0 2 
   
  But it still doesn't work. Might anybody know what is going on? Is the encrypted LVM causing additional complications?

---

### Post by maeyhem on 2009-06-10
Guess that was a total noob question.
 
I eventually discovered chown.

---

