---
title: "Howto install Dapper to hda5 and hda7 ??"
date: 2006-09-10
forum: Desktop Environments
---

### Post by lagagnon on 2006-09-10
I have a large hard disk with a number of partitions and a number of Linux distros on it. I want to install Ubuntu 6.06 / to hda5 and /home to hda7. I cannot see a way to do that with the graphical installer. It only lets me take over the entire disk or use all the remaining unused disk space. How then do I tell the installer to install to specific partitions?

Any ideas greatly appreciated.

---

### Post by FakeOutdoorsman on 2006-09-10
I'm fairly sure you can do this with the graphical installer.  During installation when you reach "Prepare Disk Space" choose *manually edit partition table*.  It will show you  alist of your partitions.  After you choose which file formats you want the next window will allow you to choose your mount points.  For example, one partition can be your linux swap partition and one can be /home and one can be "/".  Here is a page that [shows the above process]("http://www.psychocats.net/ubuntu/installing.html").

---

