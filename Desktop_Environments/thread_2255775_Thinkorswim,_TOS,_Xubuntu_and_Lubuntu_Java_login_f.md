---
title: "Thinkorswim, TOS, Xubuntu and Lubuntu Java login frame garbled."
date: 2014-12-07
forum: Desktop Environments
---

### Post by asorsher-m on 2014-12-07
Well, I got the Tos platform working properly on Xubuntu, but could not on Lubuntu.

A lil background:  6 year old Fujitsu laptop with a Core 2 duo, 4gig ram, 500 gb Samsung HD.  Dual boot Vista and Xubuntu. Also, I have a separate NTFS partition for data which can be accessed in both Vista and Linux.

After a recent update to Xubuntu 12.04 LTS, it would not boot and reported many bad blocks on that partition.  I don't know why this happened and I could not recover the partition, so I decided to erase it (Gparted) and install a newer version.  I read that Lubuntu was even faster and lighter than Xubuntu, so I gave Lubuntu 14.10 a try.  Installed fine, but I could not get Thinkorswim platform to run.  It installed fine (first installed Oracle java 7 from the webupd8 repository ppa), ran its updater, but when it switched to the logon frame, it choked with garbled video and ate up all my cpu resourced -- cpu fan went to full speed.

Long story short -  I wiped the partition again, and now installed Xubuntu 14.04.1 LTS, and TOS installed and runs fine.  I suspect the window manager in Lubuntu was not working right with the TOS java program, but the window manager in Xubuntu does.  Can anyone confirm this?

btw, I edited the TOS launcher working directory to point to the same folder that TOS uses when I run Vista (also copy the linux executable script to that folder).  This enables me to access the same TOS workspaces, chart settings and studies etc, in both Vista and Xubuntu.  Sweet!

---

