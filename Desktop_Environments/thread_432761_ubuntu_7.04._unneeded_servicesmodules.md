---
title: "ubuntu 7.04. unneeded services/modules"
date: 2007-05-04
forum: Desktop Environments
---

### Post by gray380 on 2007-05-04
Hi there!

How to me to avoid loading modules unnecessary me during start of system?
Such as  raid10,raid456,raid1,raid0,multipath,linear,sbp2,ohci1394,ieee1394,...

brg,
Serhiy.

---

### Post by Theimon on 2007-05-05
Open up a terminal and enter: ```
sudo nano /etc/modprobe.d/blacklist
```
Then add a line for each module that you want to blacklist like so:
```
blacklist raid10
blacklist raid456
blacklist raid1
```
But take caution, make sure they are indeed useless modules. Blacklisting some modules which depend on others could result in a buggy booting system.

---

