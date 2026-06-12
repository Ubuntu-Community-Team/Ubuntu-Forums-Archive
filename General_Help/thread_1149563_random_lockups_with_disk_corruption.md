---
title: "random lockups with disk corruption"
date: 2009-05-05
forum: General Help
---

### Post by dethtron5000 on 2009-05-05
Tried posting this in the 64-bit forum, but didn't get much of a response, so I'm trying here.

I'm having a recurring issue in which programs stop responding and then files get becoming corrupted. Everything worked fine in 8.10 but since I upgraded to 9.04 this has been a pretty consistent issue. The applications I've been using are firefox (over wifi), open office and rhythmbox. I'm basically running fsck every time I boot up (and in some cases the drive has been corrupted to the point that I have to run from CD and repair the boot records).  I haven't lost any data yet, but I'm concerned at this point.

I have tried running memtest and the system was just fine.

If anyone can point me in the right direction for a solution, I'd be very appreciative.

System info:
Intel(R) Core(TM)2 Duo CPU     P9500  @ 2.53GHz
NVIDIA GeForce 9600M GT driver version 180

---

### Post by kay-man on 2009-05-05
I've had similar issues with tv recordings in mythtv. In my case, it turned out to be the hard drive itself. It might be worthwile to check it. If it's S.M.A.R.T. enabled you could install smartmontools and get a lot of info.

Or at least it might help you rule out another possibility.

---

### Post by codeseer on 2009-05-05
Ext3 or Ext4?

---

### Post by dethtron5000 on 2009-05-05
> **codeseer said:**
> Ext3 or Ext4?
ext 3

---

### Post by codeseer on 2009-05-05
> **dethtron5000 said:**
> ext 3

Have you tried upgrading the Kernel?

---

### Post by wpshooter on 2009-05-05
Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu BEFORE you installed Ubuntu ?

---

### Post by dethtron5000 on 2009-05-05
> **wpshooter said:**
> Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu BEFORE you installed Ubuntu ?
I installed 9.04 via the upgrade function in 8.10...

---

### Post by dethtron5000 on 2009-05-05
> **codeseer said:**
> Have you tried upgrading the Kernel?
No I haven't - I read this post: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) but i understood it to be primarily for intel graphics card users.

---

### Post by wpshooter on 2009-05-05
> **dethtron5000 said:**
> I installed 9.04 via the upgrade function in 8.10...

The type of problems that you are referring to is the reason I never move from one version of Ubuntu (or any other O/S) to another version of Ubuntu via upgrade.  I always install the new version from scratch and I have very litte or no problems.

A word to the wise is sufficent !!!

---

### Post by dethtron5000 on 2009-05-05
> **wpshooter said:**
> The type of problems that you are referring to is the reason I never move from one version of Ubuntu (or any other O/S) to another version of Ubuntu via upgrade.  I always install the new version from scratch and I have very litte or no problems.

A word to the wise is sufficent !!!
I'd like to move my home partition on to a separate partition so I can do that easier - is there a page that documents how to do this?

or alternatively should i just reinstall off the cd?

---

### Post by codeseer on 2009-05-05
> **dethtron5000 said:**
> No I haven't - I read this post: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) but i understood it to be primarily for intel graphics card users.

Yeah, you just take step 1 there and remove the intel specific stuff.

---

### Post by codeseer on 2009-05-05
> **dethtron5000 said:**
> I'd like to move my home partition on to a separate partition so I can do that easier - is there a page that documents how to do this?

or alternatively should i just reinstall off the cd?

You just need to make a partition, edit fstab and rsync the files over. Here's a guide:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by dethtron5000 on 2009-05-07
> **codeseer said:**
> Yeah, you just take step 1 there and remove the intel specific stuff.
ok, the problem still manifests after a clean install (with the new partition configuration)...blarg.  

the nvidia stuff failed when I tried the kernel upgrade...going to try that again i guess...

---

### Post by quixote on 2009-05-18
I have this same problem, using 64-bit jaunty.  I actually filed a bug report about it ([https://bugs.launchpad.net/jaunty-backports/+bug/372526](https://bugs.launchpad.net/jaunty-backports/+bug/372526)) since it obviously wasn't normal behavior or something to do with hardware failure.

It's very frustrating.  Can't use jaunty because of it, since I never know when it's going to lock up on me and require a filesystem fsck rebuild!

My system: CPU: P8400 Core 2 duo 2.26Ghz;  Graphics: integrated Intel GMA X4500; 4GB RAM

Also, eyefragment has posted in this thread [http://ubuntuforums.org/showthread.php?t=1163584](http://ubuntuforums.org/showthread.php?t=1163584) about the same issue.

---

### Post by quixote on 2009-06-01
Looks like [we may have a fix]("http://ubuntuforums.org/showpost.php?p=7382178&postcount=29").  It involves upgrading the kernel on the jaunty install, but that's surprisingly easy to do.  At least, it was surprising for me!

---

### Post by Bearly Able on 2009-06-04
I've been having the same problem, but with 32bit Ubuntu.  I've found a temporary solution by completely removing the Nvidia driver, although that leaves me with other problems.  I'm using GeForce 7900 GS and had no trouble until I upgraded to Jaunty.

---

