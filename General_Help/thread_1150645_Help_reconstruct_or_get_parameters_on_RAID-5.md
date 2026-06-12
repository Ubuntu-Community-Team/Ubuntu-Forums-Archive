---
title: "Help reconstruct or get parameters on RAID-5"
date: 2009-05-06
forum: General Help
---

### Post by idgamerd on 2009-05-06
I was not sure were to post this so if this is a wrong category I am sorry.



First of all it should be said that I am very new to Linux. I have successfully reconstructed one RAID-5 array before using mdadm –detail to get info (block size, disk order and rotation type) then input into to UFS Explorer and it was all good but this was a VERY long time ago and I don’t remember how I did it. 
   
  Right now I have 3 out of 4 drives from a NAS (one failed). When I hook them up and do fdisk –l I get this for all three drives (* is a different number/letter drive)
   
  Device Boot       Start     End         Blocks               Id                 System
  dev/sd**                 1          13         104422             fd                 Linux raid autodetect
  dev/sd**               14          26         104422+           fd                 Linux raid autodetect
dev/sd**               27     182401       1464927187+  fd                 Linux raid autodetect
   
  What do I have to do next do get the information about the RAID? Do I have reconstruct them with mdadm? If so can some give me a commend to do it with 1 missing disk.
   
  My end goal is to somehow run mdadm –detail to get info on the order, block size, rotation, etc. These drives are from a barebone NAS with very little info about it on the web.
   
  Thank you for your help!

---

### Post by fjgaude on 2009-05-06
Here's what I would do:

```
sudo mdadm --assemble --force --scan /dev/md0
```

Use whatever the name of the array is instead of /dev/md0

I don't know how you took the failed drive out of the array. Here, mdadm is used to --fault and then --remove the drive. To add one back the --add command is used.

We can do things wrong using mdadm that leaves us in a place where we have to start over, and the drives that were in an array have to have their superblocks zeroed.

Take a look at these links:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Good hunting!

---

### Post by idgamerd on 2009-05-06
Well I did examine on the mdadm (--detail) and it shows that md3 (the data) is now RAID-0 when before it was RAID-5 (100% positive) the NAS must have did a factory restore or something by itself (definitely not a full format or anything).

Question is it is somehow still possible to restore it to RAID-5 with 1 drive NOT working?

> **fjgaude said:**
> Here's what I would do:

```
sudo mdadm --assemble --force --scan /dev/md0
```Use whatever the name of the array is instead of /dev/md0

I don't know how you took the failed drive out of the array. Here, mdadm is used to --fault and then --remove the drive. To add one back the --add command is used.

We can do things wrong using mdadm that leaves us in a place where we have to start over, and the drives that were in an array have to have their superblocks zeroed.

Take a look at these links:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)

Good hunting!

---

### Post by fjgaude on 2009-05-08
If the array is truly raid0 there is nothing I can think of to restore. Stripping, raid0, puts pieces of data on each drive that is nowhere else.

I suppose you can't mount the array and get the data off, and then recreate the whole array?

---

