---
title: "ubuntu installation"
date: 2008-06-03
forum: Desktop Environments
---

### Post by irshan on 2008-06-03
Dear Friends,

i want to install ubuntu 7.10 to my machine which is already have winxp in c partion and other partion is D not more.the D partition capacity is 10GB.so pls give me all the ways to install ubuntu to my machine.i tried but in some point which ask that 3 partion ways then i choose manual one after taht i dont know how to make it.

but i must need win xp. i want to install ubuntu in D partion.

pls help me

---

### Post by Bakon Jarser on 2008-06-03
Are you going to use the entire D: partition for Ubuntu?

---

### Post by Xiong Chiamiov on 2008-06-03
This is the forum for Desktop Environments (GNOME, KDE and the such).  You'll do a lot better over at the [Absolute Beginner's Forum]("http://ubuntuforums.org/forumdisplay.php?f=326").

You'll have to partition your "D" partition (I use the term loosely, since partitions don't *really* have letters assigned to them) into at least two other partitions, one swap (~1 gig or so) and one for the rest.  You'll want to choose a filetype of swap for the first, and ext3 for the second.

---

### Post by jualin on 2008-06-03
If you use the manual partitioning option you should create a / partition and a swap partition with ext3 formats and swap format respectively. So basically you will divide your 10 GBs in lets say 1GB for your Swap partition and the rest for the "/" partition. The "/" is the mount point, and you access this by right clicking on the partition that you want to format (D 10GB) and then Edit. Hope this takes you in the right direction. 
P.S. Be careful you dont choose your Windows partition and erase windows. Just make sure that you know the size of both partitions so you can differenciate them.

---

### Post by irshan on 2008-06-03
i made as u said but it is given following error msg
 "windowswindow~1.log is 496k,but it has 92 clusters(736k).what is mean it.

---

### Post by houssam.chahine on 2008-06-03
look there is a very simple way.you can install ubuntu on the C directory (it will be installed in the free space of the C partition). Besides I recommed you to remove winxp and install ubuntu 7.1 and in case u need to use win xp u can use the virtual box and install winxp on it.

---

### Post by jualin on 2008-06-03
irshan I have never encountered that error before but I am guessing is because some file got corrupted during the installation. I would try again and make sure you select the "format" check box also in the "/" partition. Now the only problem with Houssam.chahine advice is that Virtual Box doesnt do everything like gaming for example, so if one day you decide to play a game on your computer or to use a very resource demanding windows application you may need to have a real copy of Windows installed in your computer. But this is just preference. In my case, I dual boot XP and Ubuntu. Most of the time I use Ubuntu but sometimes I am forced to use Windows. Good luck!

---

### Post by Bakon Jarser on 2008-06-03
> look there is a very simple way.you can install ubuntu on the C directory (it will be installed in the free space of the C partition).

A problem with this suggestion is that we don't know how big or how much free space his windows partition has.

---

