---
title: "How to partition? Partitioning for swap?"
date: 2009-02-22
forum: General Help
---

### Post by tbi on 2009-02-22
Hi, this is my first post on this forum and likewise my first attempted installation of the Ubuntu operating system and I was wondering if anyone could give me a little advice before I go ahead and start partitioning. 

My situation is this. 
At the moment I have a 150GB hard drive partitioned as follows: 8GB EISA configuration files on one partition and another 142GB for the vista operating system and any other personal files and programs etc.

I want this Hard drive set up to dual boot with a shared area for general files, my current 'planned set up' being as follows.
1st partition = 8GB, EISA config files
2nd partition = 60GB, Vista operating system (NTFS)
3rd partition = 10GB, Ubuntu operating system (EXT3)
4th partition = 2GB, Swap partition
5th partition = 70GB, general shared files and other (NTFS)

I was going to accomplish this like this:
1.De-fragment the current vista partition to ensure nothing gets messed up later on.
2.Use the vista tools to shrink the partition down to 60GB
3.create the 12GB partition for Ubuntu and its swap
4.create the 70GB partition for the general shared files
5.Boot Ubuntu from a Live installation cd installing it to its partition and letting it partition its own 2GB for swap.
6.Have GRUB installed in front of Ubuntu rather than at the MBR
7.Use EasyBCD to add Ubuntu as an entry to the boot up.


What I would like to know is if there are any obvious problems in my 'plan'? 
Have I done anything wrong? and could I do anything better? 

Also does a partition need to be created for swap before installing Ubuntu or does it have to be created through the LiveCD installer?

If anyone could give me any advice I'd be extremely grateful. Thanks.

---

