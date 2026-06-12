---
title: "new to linux"
date: 2009-06-16
forum: General Help
---

### Post by amir aljaberi on 2009-06-16
hi
first i m new to linux so i wanna switch to it and i have msi laptop with 1.6 C7-M via processor, ram 3gb and hdd 320 so can u tell me plz whcih ubuntu version is suitable for me ? :(

thx;)

---

### Post by ActiveFrost on 2009-06-16
Jaunty ( current, 9.04 ) should work on any PC ( "should" does not always mean that it will ). Try it ;)

---

### Post by Legace on 2009-06-16
Jaunty or Jaunty UNR.

---

### Post by TrakerJon on 2009-06-16
This post should help you as well...

**[http://ubuntuforums.org/showthread.php?t=1181327](http://ubuntuforums.org/showthread.php?t=1181327)**

---

### Post by amir aljaberi on 2009-06-16
hi 
plz where can i find jaunty version?

---

### Post by bruce2000 on 2009-06-16
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Choose Ubuntu 9.04 - that's Jaunty

---

### Post by amir aljaberi on 2009-06-16
oh, very quick respose 
thx for ur help
 but plz which one desktop ed or nrtbook ed or sever edition

---

### Post by izizzle on 2009-06-16
Desktop edition, since you're on a laptop.

---

### Post by desiDragon on 2009-06-16
I would assume desktop one should be good. the netbook one is for the smaller "mini" laptops. such as the dell mini 9

---

### Post by amir aljaberi on 2009-06-16
no mine is notebook with combo dvd and 13.3" (msi vr321) so plz netbook or desktop edition ?

---

### Post by bruce2000 on 2009-06-16
You probably want the desktop edition, the server one comes with no GUI

I've not had any experience with the netbook version, on my laptop ive used the desktop edition. It seems to be enhanced for the small screens on notebooks. You say yours is a laptop so i would go with the desktop edition.

---

### Post by amir aljaberi on 2009-06-16
yeah mine is laptop so i ll get desktop edition
thx all for ur help

---

### Post by bruce2000 on 2009-06-16
You're welcome, if you run into any problems installing it just post back here.

---

### Post by desiDragon on 2009-06-17
I installed the desktop version on my mini (9") and then installed the netbook remix via the terminal

"sudo apt-get intall ubuntu-netbook-remix"

this way I can switch back and forth if I wanted.

Installing netbook alone using the ".img" from the website wasn't too much of a success for me. But what I mentioned above works for me.

Hope that helps.

---

### Post by amir aljaberi on 2009-06-21
hi 
which is better type of partition to instal ubuntu on it? is it fat32 or ntfs ? or ubuntu cd will format the partition to ext3/ext4? 
and can i read/write ext3/ext4 from widows?

---

### Post by bruce2000 on 2009-06-22
> **amir aljaberi said:**
> hi 
which is better type of partition to instal ubuntu on it? Is it fat32 or ntfs ? Or ubuntu cd will format the partition to ext3/ext4? 

Will your installation be a dual-boot? In that case yes the ubuntu cd will give you a choice of either ext3 or ext4 (I've heard of some people having stability problems with the newer ext4 so i recommend ext3)

> and can i read/write ext3/ext4 from widows?

Not directly but there is software available for windows which can do this, for example [http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by amir aljaberi on 2009-06-23
thx for ur help 
plz do i need to make partition for /boot or its not [[COLOR=black]necessary[/COLOR]]("bword://BAB!ALL!,necessary/") ?
basicaly i planned to make partions like that:
100 gb ntfs for windws
35 gb for ubuntu / and i m confused about ext3 or ex4  
5 gb swap
100 ntfs shared
60 ntfs shared
thx

---

### Post by bruce2000 on 2009-06-23
Your list of partitions looks fine to me, no need to make one for /boot

ext4 is the newer/faster file system but some people have had problems with bugs in it. ext3 is tried and tested and probably more stable, youre better off with this imo

Remember to install windows first and backup your data before working with partitions

---

### Post by amir aljaberi on 2009-06-25
hi there 
i ve installed ubuntu but i didnt make mount point for ntfs partition.
now i installed and enabled ntfs-config and now what should i do ?
and what about drivers of laptop how to install them ? 
and why ubuntu is slow to response and browsing application?

thx for ur help :D

---

### Post by Leslie Viljoen on 2009-06-25
Are you sure there's no mount point? You shouldn't have to install anything extra, ubuntu normally auto-mounts all the other partitions on the system. Check in Places -> Computer.

---

### Post by amir aljaberi on 2009-06-25
hi now i can read/write ntfs partition without making mount point, i just installed ntfs-config. in places i can found all partition and browse it.
but why ubuntu so slow and low performance ? and what about other drivers like via chrome graphics and sound card, do i need to install them?

thx

---

### Post by bruce2000 on 2009-06-26
> **amir aljaberi said:**
> hi now i can read/write ntfs partition without making mount point, i just installed ntfs-config. in places i can found all partition and browse it.
but why ubuntu so slow and low performance ? and what about other drivers like via chrome graphics and sound card, do i need to install them?

thx

Sound normally works out-of-the-box so you shouldn't need a driver, is it not working properly?

Slow performance could be caused by the graphics card driver.. but i'm not familiar with your card (you would be better off starting a new thread about this, then maybe someone with the same graphics card can help you out)

You might want to try turning off visual effects as this can slow things down, its found in System/Preferences/Appearance

---

### Post by amir aljaberi on 2009-06-27
hi there 
yes, I've opened new thread. however, they told me that via drivers not supported linux OS and aslo my ubuntu crashed many time :confused:. so  i return back to xp os :(.
and this is the thread:
[http://ubuntuforums.org/showthread.php?t=1196730](http://ubuntuforums.org/showthread.php?t=1196730)

thx a lot for ur help :KS

---

### Post by philcamlin on 2009-06-27
its not thats its not suported its you need to "tweak" :popcorn:
:P:P
when you ever get ubuntu working right you will never turn back

---

### Post by bruce2000 on 2009-06-27
> **amir aljaberi said:**
> hi there 
yes, I've opened new thread. however, they told me that via drivers not supported linux OS and aslo my ubuntu crashed many time :confused:. so  i return back to xp os :(.
and this is the thread:
[http://ubuntuforums.org/showthread.php?t=1196730](http://ubuntuforums.org/showthread.php?t=1196730)

thx a lot for ur help :KS


That's too bad but at least you gave it a try :)

---

