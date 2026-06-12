---
title: "Trouble instlaling Steam on Ubuntu 15.04"
date: 2015-09-20
forum: Gaming &amp; Leisure
---

### Post by andrew257 on 2015-09-20
Hello, I am currently trying to install steam but it is failing to launch after I installed it.  I am running Ubuntu Gnome 15.04
I installed steam with *sudo apt-get install steam*

Here is the error message I get when I try to launch it:

> 
> steam &
[2] 4041
Running Steam on ubuntu 15.04 64-bit
STEAM_RUNTIME is enabled automatically
[2015-09-20 11:43:56] Startup - updater built Aug 19 2015 11:27:40
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)


What is causing the issue and how can I fix it?

Specs if they matter:  Desktop running Ubuntu Gnome 15.04, i5 4670k, R9 280X.

Update:
I searched the problem I am having and some people said that a  proprietary GPU driver needs to be installed.  After I installed the driver, I restarted the system for good  measure.  What happened was that the system failed to load graphics  properly.  I could only do anything by either booting into recovery mode  and/or using the command line.  So after an hour and a half, I finally  managed to get the graphics working again by removing steam, changing  back to the open source drivers, and repairing packages in recovery  mode.  This gets me back to square one.

---

### Post by Bucky Ball on 2015-09-20
*Thread moved to **Gaming & Leisure**.*

You may have better luck here. ***Installation and Upgrades*** is for the Ubuntu OS. :)

---

### Post by andrew257 on 2015-09-20
Bump + update:

I searched the problem I am having and some people said that a proprietary GPU driver needs to be installed (I have an R9 280X if that helps).  After I installed the driver, I restarted the system for good measure.  What happened was that the system failed to load graphics properly.  I could only do anything by either booting into recovery mode and/or using the command line.  So after an hour and a half, I finally managed to get the graphics working again by removing steam, changing back to the open source drivers, and repairing packages in recovery mode.  This gets me back to square one.

---

### Post by QIII on 2015-09-20
Did you do 

```
sudo amdconfig --initial
```

after installing the driver and before restarting?

By the way, there is an oddity that requires that Steam be installed before the fglrx driver is installed.

---

### Post by andrew257 on 2015-09-20
Steam appears to be working and the computer is capable of restarting without issue.  I am going to guess that my problem is solved.  Thanks for the help!

---

### Post by QIII on 2015-09-20
@andrew257:  It would be very helpful to others if you would explain just what it was that made this work.

Someone else may have the same problem and find this thread while searching for a solution.  With no explanation, it would just be another dead end.

---

