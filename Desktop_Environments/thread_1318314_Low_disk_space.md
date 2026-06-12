---
title: "Low disk space"
date: 2009-11-07
forum: Desktop Environments
---

### Post by lukereimer on 2009-11-07
Hi there, 

So I just installed 9.10 on a 64-bit desktop machine a few weeks ago so it's a relatively fresh install... I have a few extra software packages installed but nothing huge. 

I got a critical disk space error today saying I only have 800MB of space remaining. Sure enough, when I check in the Linux filesystem it also says I only have 800MB remaining. 

The problem is that I have ubuntu installed on a 250GB internal hard drive... There should be boatloads of space. I checked using a linux partition manager as well as from a windows partition manager (I have two internal hard drives, dual boot) and both partition managers showed the Linux drive as having tons of free space. 

I can hardly get into my ubuntu drive now with this critical space issue... Why does it think it has no space? Any ideas? 

Update: Output of "df -k" command: 

[IMG]http://fluidmedia.ws/screenshot_002.png[/IMG]

Thanks!
Luke

---

### Post by lukereimer on 2009-11-15
I am very sorry to bump... But I can't use my Ubunutu whatsoever with this problem still existing - it's critical to any use of the system. 

If anyone can take a look into this, preventing me from doing a full re-download and re-installation, I would seriously appreciate it! 

Save me from using Vista!

---

### Post by drs305 on 2009-11-15
Check the "Disk Space" link in my signature line. It describes methods to find out what is taking up the space. Normally it is unemptied trash (including root's) or backups made to the system partition instead of to the backup drive.

---

### Post by drs305 on 2009-11-15
Double post, deleted.

---

### Post by lukereimer on 2009-11-15
Thanks drs, I'll check it out ASAP. Although it seems unlikely that unemptied trash and logs could take up over 200GB of space.. :S

---

### Post by lukereimer on 2009-11-19
Okay, so I looked into the disk space issue and got gParted - analyzed my partitions and such. Here's a screenshot...


[IMG]http://img39.imageshack.us/img39/6008/screenshot003h.png[/IMG]


It looks like my ubuntu is installed on this /dev/loop0 partition... when it SHOULD be on the /dev/sdb1 which has 300GB and is essentially empty. 

Does anyone know what this /dev/loop0 piece is, why it happened, and if there's a remedy past a full re-install? 

Thanks very much, 
Luke

---

