---
title: "kde4 memory leak"
date: 2011-06-28
forum: Desktop Environments
---

### Post by abracadaver on 2011-06-28
I just upgraded from 10.04 to 10.10 to 11.04.  From a reboot, if I login to KDE and run top, the memory usage for 'kde4' will slowly creep up until the system is unusable.  After about an hour it is at 80% memory usage.

Any ideas on how to troubleshoot this (i.e. find out what specific piece or component is causing the problem)?  I have disabled 'nepomuk' and the only thing that I have specifically added to startup is 'yakuake'.

Thanks!
-Shawn

---

### Post by FormatSeize on 2011-06-28
The jump from 10.04 to 11.04 is rather large for some systems. My machine can run Kubuntu 10.04 with no problems, but trying to run 11.04 was a disaster. I doubt I even got it to run for five minutes, because my hardware simply can not handle it. 
 
What hardware do you have?

---

### Post by abracadaver on 2011-06-28
It's pretty old hardware, Dell Inspiron 1521, probably:

AMD Sempron 3600+ / 2.0 GHz 
2.0 GB RAM
ATI RADEON Xpress1270

But that isn't the issue as I see it.  If I boot and don't login all is fine.  If I login to KDE all is fine for a while.  If I login and do NOTHING, just let the system sit, then the mem usage of the 'kde4' process grows and grows and grows.  This should not be the case while doing nothing.  When I first login and let things settle, 'kde4' is at about 1% mem usgae.  After an hour or so it is at 80%, while doing NOTHING and having never opened an application, clicked the mouse or done anything.  Also, I have all desktop effects off.

---

### Post by ankspo71 on 2011-06-29
Hi,
Here is a recent post that suggests it could be a problem with power management. Try turning off your power management settings to see if it helps. [http://forum.kde.org/viewtopic.php?f=17&t=95514](http://forum.kde.org/viewtopic.php?f=17&t=95514)
Hope this helps.

---

### Post by abracadaver on 2011-06-29
> **ankspo71 said:**
> Hi,
Here is a recent post that suggests it could be a problem with power management. Try turning off your power management settings to see if it helps. [http://forum.kde.org/viewtopic.php?f=17&t=95514](http://forum.kde.org/viewtopic.php?f=17&t=95514)
Hope this helps.

Thanks!  That seemed to do the trick!  I had googled kde4 memory and memory leak and hadn't run across this.  I use this laptop as a desktop and the battery went bad a year or more ago anyway.

Thanks again!

---

