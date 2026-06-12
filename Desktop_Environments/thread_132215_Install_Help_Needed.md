---
title: "Install Help Needed"
date: 2006-02-17
forum: Desktop Environments
---

### Post by khalidmian on 2006-02-17
Hi
Im a newbie at this so i apolgise for any question which may sound stupid. 
I have windows Xp and my H/D has 2 partitions one meant for the swap and the other meant for Ubuntu.
I wish to now which specific ISO file/files do i require to download inorder to install Ubuntu. I have tried the ubuntu-5.10-install-i386 file and wrote the ISO file using Nero on a CD, however the install gave various package eroors and i was unable to install. Am I downloading the right file or do i need more files?
Also I really dont know whether the root ought to be in the swap partitio or not. Someone has advised me to use GRUb for dual bot option. Can someone explain to me in non tech terms without any jargons on what I should do for proper installation?
Thanks for listening and help!

---

### Post by jpkotta on 2006-02-17
You only need the .iso that you have, and I assume that you burned it as an image. However, it is possible that it was corrupted.  On the page that you downloaded the iso from, there should be an md5sum file for the iso.  This is a checksum that serves as an integrity check on the iso.  Go [here]("http://www.etree.org/md5com.html") for a windows md5sum utility.  It's always a good idea to do an md5sum on things like install CDs, because they *must* be correct.

A simple partition scheme is:
/: 5-15 GB
swap: 1-2 x ram
/home: the rest

By saying 2 partitions, I hope you mean 2 free partitions, because Windows must be on its own partition.

/ should not be on the swap partition.  In fact, I think that's pretty much impossible (the converse is possible, though).  It's faster to put swap on it's own dedicated partition.

I like to put /home on it's own partition so I can install more than one distribution and not have to worry about it getting messed up.

Ubuntu uses GRUB by default.  It should find Windows and automatically set up a dual boot.  If not, it's not hard to fix manually.

---

### Post by khalidmian on 2006-02-18
I would like to know how exactly to run md5sum check. As for the two partions that i had created one is 320 Mb which i have kept for the swap as my RAM is also 320 MB is is a non formatted basic partition at the moment.
The other partition is 8GB which is again non formatted basic partition for /.
I have no partition creation for /home, I hope that its not an issue.

---

### Post by jpkotta on 2006-02-19
You don't need to make a new partition for /home if you don't want to.  If you really wanted, you could have the whole OS (including swap) on one partition, like Windows, or you can have more than 18 partitions (which is the maximium for IDE drives, I think).  

Get md5sum.exe from the link I posted.  Put it in the same directory as the .iso file.  Start up a DOS box (Start -> Run -> cmd).  cd to the directory containing the iso and md5sum and enter the command ```
md5sum *iso_file*
```  I think the command shell supports tab completion, so you don't have to type the whole name.  It should calculate for a while and spit out a number, which you can compare to the md5sum file on the download site.

---

