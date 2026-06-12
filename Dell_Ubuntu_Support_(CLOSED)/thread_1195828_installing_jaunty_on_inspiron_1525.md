---
title: "installing jaunty on inspiron 1525"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DeAviator on 2009-06-24
hey guys! i got my lappy dell inspiron (1525 2.0Ghz, NVIDIA card, 2 GB ram..) last yr with vista pre-installed .. at present i'm workin with dual boot n pre-partition.. now i want to know that if i get the new iso-released (ubuntu 9.04 for dell) 

1.will the setup configure everything according to my system (coz i dont want to keep debugging hardware config )
  
2. can i install vista on other partitions. 

3. can i access the derive which contains ubuntu when running vista (or the other way round)

guys if you've tried out the new jaunty please do reply

---

### Post by coffeeaddict22 on 2009-06-25
Hi,
Welcome to Ubuntu!
1) Drivers shouldn't be too much of a problem, although there are a few known issues, especially in graphics.  Easiest way to find out is to get the CD, and boot up on it.  Linux allows you to see what it's like without installing(choose the live CD option); this should show you where any issues will be.

2) Windows of any version can be put on a separate partition no problem.  There are some simple rules to make life easier for you; the best dual- boot guides I'm aware of is the APC ones [here. ]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm")  Basically, assume Linux will be ignored and you get there.

3) Linux has a heap of partition options.  The proprietary operating system you've been on can only read the 2 options developed for it.  Default install adds two partitions; one for the swap file, and one for the OS and all your stuff.  Once you've installed, setting up any other already existing hard drive partition to be able to view it is reasonably easy (if it doesn't get done automatically).

One work around is to add a partition for your /home folder in Linux, instead of just putting the whole OS in one partition; that way you can use a more intelligent filesystem (default is currently ext3, ext4 is getting close to server specs) for the OS, and one that another OS can read for your home partition.  It also means if you reinstall Linux- say, try out another distribution, or mess it up too much- you don't have to have backed up all your home files first.

---

### Post by DeAviator on 2009-06-25
k thank u..
i know bout live Linux..but iso is around 1.8 gb ..is it goin to create any problem in virtual boot using Qemu.. 
i 'll try out as u said and get bk to u..

DeAviator

---

### Post by coffeeaddict22 on 2009-06-27
Ubuntu only requires a CD for the install unless you're installing multiple language options (I believe).

---

