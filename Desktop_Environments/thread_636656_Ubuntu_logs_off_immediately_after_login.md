---
title: "Ubuntu logs off immediately after login"
date: 2007-12-10
forum: Desktop Environments
---

### Post by raghukr on 2007-12-10
Finally, installed ubuntu 7.10 on my machine with configuration below

AMD Athlon 2800+
256 MB ram
Samsung CDRW
Seagate 80 GB HDD
ext3 partition ~3GB
swap ~340MB

I am facing a problem now. Once I login, the desktop appears, but immediately logs out - back to login screen. I am able to login to failsafe gnome session, but not to normal gnome session. Please suggest what might be wrong?

---

### Post by kishorebudha on 2007-12-10
I had this problem after I installed ATI drivers using the instructions given here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

 I even reset Xorg.conf. Did not help. Had to ultimately reinstall Ubuntu.

I would be keen to know if and how this problem was sorted out.

---

### Post by raghukr on 2007-12-17
I installed the ATI graphics driver, and the problem is now gone. I Just ran the ati-driver-installer-7-11-x86.x86_64.run directly and allowed it to do the installation for me instead of following steps in the guide. It has a text based UI and did the job nicely.

---

