---
title: "Disk Space Check"
date: 2005-03-29
forum: Desktop Environments
---

### Post by faddat on 2005-03-29
This week I was treated to a large, unexpected system crash due to my incessant tendency to download large files.  It filled /home, and my system didn't tell me that /home was full.  The result was my MEPIS system no longer booting.  I could boot a Kubuntu liveCD, but not install Kubuntu using the installer.  It would install, but then die shortly after I entered my username/password when it was trying to write to /home.  

The lessons I've learned from this are many, but I think that there a few that could be useful to the Gnu/Linux community:

1.  Check available space in /home during installs.  Warn if it's below 100MB.
2.  Make available disk space something that the user regularly interacts with.  A pie chart ala MS windows could be useful.  

The first one would keep others from fruitlessly reinstalling linux very confused.  It'd also be one of those things that would just make life easier on the newbie.  The second thing is a consideration until disks are of an infinite size.  Essentially, though, my system went out from under me and I didn't know why.  

My $.02.  

(Now running Kubuntu, loving it)

---

### Post by dermotti on 2005-03-29
There should be some sort of preinstalled warning system imho, its happend to me too, luckly i figured out what hte issue was.

---

### Post by ubuntu_demon on 2005-03-29
1 diskmonitoring is planned for breezy. i don't know if they are going to check for free space too.  [http://www.ubuntulinux.org/wiki/DiskMonitoring](http://www.ubuntulinux.org/wiki/DiskMonitoring)

2 I use xdiskusage to see where my space went.

---

### Post by dermotti on 2005-03-29
is that a package we can get via apt-get?

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=dermotti]is that a package we can get via apt-get?[/QUOTE]
 sudo apt-get install xdiskusage

you have to start it as root / with sudo to be able to scan the whole drive. But if you don't sudo you can still use it ofcourse.

---

### Post by crane on 2005-03-29
The best thing to do would be to determine how much space you have total on your disk the allocate a set amout of space for you /home directory. That way if your home directory gets full, the entire hard disk is not full and the system still has space to run on.
This is why a lot of people put their /home directory in a different partition.
Just my .02 as well.

---

### Post by ubuntu_demon on 2005-03-30
[QUOTE=crane]The best thing to do would be to determine how much space you have total on your disk the allocate a set amout of space for you /home directory. That way if your home directory gets full, the entire hard disk is not full and the system still has space to run on.
This is why a lot of people put their /home directory in a different partition.
Just my .02 as well.[/QUOTE]
 This is the easy way of partitioning. I use it myself. You've got to at least have the partitions :

swap (1-3 times the amount of physical ram you have dependend on how much ram is going to be used, use 2 times the amount of physical ram if you are unsure)
/ (3-5 gb dependend on how much space you have in total and whether you are planning on installing a lot of extra software like games)
/home (the rest of your space)

But partitioning isn't always as easy as it sounds. The way I think is hard is partitioning for the following partitions. I haven't done it myself because I was afraid I would get it wrong and waste too much space. But the method has advantages. More security and if there's something wrong and your tmp or var gets bulky you know it earlier than you would have otherwise.

swap (1-3 times the amount of physical ram you have dependend on how much ram is going to be used, use 2 times the amount of physical ram if you are unsure)
/ (1 gb?????)
/usr (2-4 gb???? here's where your software gets installed)
/tmp (1 gb ????)
/var (1 gb ????)
/boot (at least 100 mb?)
/home (the rest of your space)

Please correct me here if you would do it different.

Maybe LVM is cool. I just know it exists. I haven't really looked into it.

---

### Post by fdoving on 2005-03-30
You should try 'kwikdisk' in the 'kdf' package (apt-get/kynaptic).
It'll give you warnings when one of your filesystems gets critically full.. 

After installing the package.. alt+f2 'kwikdisk'.. and you'll get another nice icon in your systray.


Enjoy.

---

