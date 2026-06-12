---
title: "A bug in the installer"
date: 2005-11-08
forum: Desktop Environments
---

### Post by TmP on 2005-11-08
I bet you alredy found this out but here goes:
Its both in Hoary and Breezy

While partitioning the disk, I've tried to create a /home part. that would be accesable both to Ubuntu and win. I've set the filesystem to fat32. The partitioner didint complain, so I continued the installation. Than while creating new user, the installation falls into a loop: It asked me for the username login and password and after confirming, kept asking the question again. Than when I pressed esc and reentered, it only asked me about the root password. When the system ran, and the prompt appeared asking me to log on, it keapt denying me any of the logins or passwords I've put in during the loop. And since root login is disabled by default, I found myselfes stuck. 

Keeping  partition with /home in ext3 solved the problem.

Seriously, the installation is the most important thing when it comes to making window's users recognise Ubuntu as an alternative. I find a graphics installer with a selection of predifined partition sets (/ /swap /home) an absolute necessity.

ThanX!

P.S. I dont really know how to report it officially since I'm not familiar wit bugzilla, so if anyone could do it for me I'd be glad

---

### Post by az on 2005-11-08
[QUOTE=TmP]
Seriously, the installation is the most important thing when it comes to making window's users recognise Ubuntu as an alternative. I find a graphics installer with a selection of predifined partition sets (/ /swap /home) an absolute necessity.

ThanX!

P.S. I dont really know how to report it officially since I'm not familiar wit bugzilla, so if anyone could do it for me I'd be glad[/QUOTE]

By default, everything goes onto one partition.  Unless you manualy edit the partition table, you will not have this problem.  You do not really need to have seperate partitions.  So, most users will not have this problem.

As for competing with windows, it is more difficult to install windows than to install ubuntu.  The next release should include ubuntu-express which will run off a live cd.  That will make it even more impressive and easier.

If you are able to figure out how to partition your drive, it should not be too difficult to figure out bugzilla.  Please file a bug about the installer not complaining about putting home on a fat partition, since that is a real problem.  

The important part about filing a bug is following up on it.  I checked and there are no similar bugs for the installer already filed.

bugzilla.ubuntu.com

---

