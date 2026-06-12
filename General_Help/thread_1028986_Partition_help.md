---
title: "Partition help"
date: 2009-01-02
forum: General Help
---

### Post by ryclegman on 2009-01-02
hello,

I would like to change the size of my Linux partition. I tried gparted and when it went to boot it got an error that the link was slow to respond ect... So then i went over to my windows partition and and tried doing it there but it wouldn't let me resize at all.. it would allow me to modify my windows partition but not the Linux. and in ubuntu i wasn't able to modify the linux partiton either... only the windows. I want to make my windows a bit bigger, and the linux side a bit smaller. For some reason i just cant modify the Ubuntu partition at all... I dont know why the gprated iso wouldn't work either... may be because i have a 64bit computer?

specs..
-500 gig sata
-intel quad core 64bit
-4gigs of memory
-nvidia 9600gt
-msi motherboard

Thanks 
Ryan

---

### Post by logos34 on 2009-01-02
try gparted on the ubuntu live cd (system>admin>partition editor)...If you could, post your 

sudo fdisk -l

output.  Sometimes if ubuntu is inside an extended partition you can't resize / because the live cd mounts the /swap partition, locking the entire partition up until you turn it off.

---

### Post by 2hot6ft2 on 2009-01-02
> **ryclegman said:**
> hello,

I would like to change the size of my Linux partition. I tried gparted and when it went to boot it got an error that the link was slow to respond ect... So then i went over to my windows partition and and tried doing it there but it wouldn't let me resize at all.. it would allow me to modify my windows partition but not the Linux. and in ubuntu i wasn't able to modify the linux partiton either... only the windows. I want to make my windows a bit bigger, and the linux side a bit smaller. For some reason i just cant modify the Ubuntu partition at all... I dont know why the gprated iso wouldn't work either... may be because i have a 64bit computer?

specs..
-500 gig sata
-intel quad core 64bit
-4gigs of memory
-nvidia 9600gt
-msi motherboard

Thanks 
Ryan
The reason is that you have the partition mounted and you're trying to change it. It has to be unmounted that's why everyone says to use the livecd to make partition changes.

And what logos34 said too.

---

### Post by ryclegman on 2009-01-03
ok here is my output 

> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11011100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19365   155549331    7  HPFS/NTFS
/dev/sda2           19366       60801   332834670    5  Extended
/dev/sda5           19366       59323   320962603+  83  Linux
/dev/sda6           59324       60801    11872003+  82  Linux swap / Solaris


and iv attached a screenshot of what im trying to do.
i want to move that unallocated space to windows partition. The space is stuck in the extended partition lock.

---

### Post by scradock on 2009-01-03
Yes, that's the trouble. You can't take that space out of the extended partition while either the linux partition or the linux swap partition is mounted.

2 ways to proceed - either use the liveCD, run the command sudo swapoff and then reduce the size of the extended partition, finally increase the size of the windows partition;

OR - rather simpler to do, why not simply create a new NTFS (or even FAT32) partition in the unallocated space in the extended partition? Windows will see that as available space in a second "drive" (D:) and you will have some spare capacity if that's what you need. Easy to use for media storage, a bit harder to set up programs, but it can be done.

HTH

---

### Post by ryclegman on 2009-01-03
I think im going to follow this way. 
> 2 ways to proceed - either use the liveCD, run the command sudo swapoff and then reduce the size of the extended partition, finally increase the size of the windows partition;
When i run the swap off i get this
> ubuntu@ubuntu:~$ sudo swapoff
usage: swapoff [-hV]
       swapoff -a [-v]
       swapoff [-v] special ...

I am not able to change the size of the extended partition, only the partitions inside of the extended lock 

is their any command i can use to "unlock" the extended partition...

---

### Post by ryclegman on 2009-01-03
ok got it thanks for everyones help!

its going though its long process now :]

---

### Post by Irony on 2009-01-03
Just drag the left side of the unallocated parition to the right. Note switch off swap (if its on) by right clicking on swap and turning it off.

Now drag the right side of the first partition to the right.

Note perform each operation one at the time or else gparted will seize up.

This of course is all done from the live CD.

---

### Post by ryclegman on 2009-01-03
Gparted will size up? Its been going for a couple hours how and still has a long ways to go. I have it doing everything right after another... is that bad? an i am doing it from ubuntus live cd... if you mean by it taking up memory, i hsve 4gigs of it so it should be fine.

---

### Post by logos34 on 2009-01-03
whenever you grow the left side of a partition it takes a lot longer--all the files have to be copied and moved over.

---

### Post by ryclegman on 2009-01-03
It went great no problems at all!

---

