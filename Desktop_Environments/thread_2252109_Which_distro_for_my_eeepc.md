---
title: "Which distro for my eeepc?"
date: 2014-11-09
forum: Desktop Environments
---

### Post by Byb on 2014-11-09
Hi all
The  beast has 4GB SSD + 8GB sdcard + 2 GB RAM.... and is currently running an erratic eeeubuntu3.


Thanks

---

### Post by sudodus on 2014-11-09
You want something that installs nicely into the small SSD, and I think the standard installers want more than 4 GB drive space. Maybe you can try with the OBI or OBI-9w and install a system that is small in the beginning, but can be built into different sized final installed systems. See

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

and install **Trusty-nonpae-txt5.tar.xz**

or see

[https://help.ubuntu.com/community/9w](https://help.ubuntu.com/community/9w)

and download [http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso](http://phillw.net/isos/linux-tools/9w/obi_Trusty-nonpae-txt5-9w.iso)

and from that install **Trusty-nonpae-txt5**

which comes with a text based menu, where you can select different desktop environments, for example a simple window manager or a full Lubuntu system. The sizes of the available systems are listed at

[https://help.ubuntu.com/community/9w/RAM_%26_disk_usage](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage)

e.g. Lubuntu will use 2.8 GB (with the restricted extras installed)

-o-

Installing from USB pendrives is described in the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by coldraven on 2014-11-09
I installed Xubuntu onto my eeePC 900 but it almost completely filled the 4GB drive. I had /home on the 16GB drive. It worked fine but ran out of space when it came to update. The problem was that the /tmp directory had no space to uncompress all the packages. So to fix it I moved /tmp and /var to the 16GB drive. I don't have this PC any more so I don't know how it's working now.
If you want to update the BIOS (for the eeePC 900) I have posted about it here:
[http://ubuntuforums.org/archive/index.php/t-2195898.html](http://ubuntuforums.org/archive/index.php/t-2195898.html)

---

### Post by Rob Sayer on 2014-11-09
How about the ubuntu minimal install cd then lxde-core?

---

### Post by oldrocker99 on 2014-11-09
Puppy Slacko runs off a USB drive, and doesn't use your hard drive, and is tiny and FAST.

---

