---
title: "gparted 0.2.5 in ubuntu?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by manutremo on 2006-07-16
I have just had to resize some partitions in my hd and found that it's not possible with the 0.1 version of gparted that is installed in ubuntu.

I finalle did the work with Partition Magic from Windows with no problems, but then I had to boot with the liveCD to make some adjustments... and found that the version in the liveCD is much newer and has more options.

I have downloaded the source of the latest gparted and tried to compile, but is giving me an error "libuuid is missing" when i ./configure. libuuid is part of ef2progs, which is installed in my machine, so I suspect some version problem (which I can0t resolve as the installed version is the latest 1.38) ](*,) 

I have tried to install the debian package but it gives more dependencies errors :-k 

Before starting to install all the new revisions of the needed libs manually... Anyone knows if we can have a Ubunut package with a more recent version of gparted? Thanks!

---

### Post by cotcot on 2006-07-16
I use the GParted LiveCD for partitioning. It does a better work than gparted from the Applications in ubuntu.

---

### Post by stanz on 2006-07-16
> **cotcot said:**
> I use the GParted LiveCD for partitioning. It does a better work than gparted from the Applications in ubuntu.
Not being a tech-ie...I agree.
I've went and downloaded GParted form their [homepage]("http://gparted.sourceforge.net/") @ sourceforge, then... burnt it to a mini disk, so I always have it ~ seperate, ~ from my re-installs. :mrgreen:
This all works great - from **boot**.
Since I can insert disk & reboot...and work whatever tweaks I want _"without any OS's running!"._
I hopes this all helps ! 8)

---

### Post by beameup on 2006-07-16
And don't forget the System Rescue Disk. It's always better to do it from boot. 

[http://www.sysresccd.org](http://www.sysresccd.org)

---

