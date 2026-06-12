---
title: "Would like to make a partition that can be read by both windoz and ubuntu"
date: 2009-03-25
forum: General Help
---

### Post by yergeht on 2009-03-25
I now I should prolly use gparted from a live cd but I don't know the commands for gparted to do that...

---

### Post by mb_webguy on 2009-03-25
GParted is a GUI application, so doesn't use "commands".  Making a new partition is fairly straightforward, assuming you have space available on the drive.  Otherwise, you'll have to try to shrink and existing partition.  Format the partition as either ntfs or ext3 (and use the [ext2ifs]("http://www.fs-driver.org/") driver in Windows) to make the partition usable by both OSes.

---

### Post by kanikilu on 2009-03-25
Commands? gparted is a GUI to parted. It's just point-and-click...

Check out the manual, and if you have specific questions, just ask:

[http://gparted.sourceforge.net/manual/gparted_manual.html](http://gparted.sourceforge.net/manual/gparted_manual.html)

---

### Post by Kareeser on 2009-03-25
sudo apt-get install gparted

---

### Post by mb_webguy on 2009-03-25
> **Kareeser said:**
> sudo apt-get install gparted

Since you shouldn't attempt to do partition changes on a mounted drive, it's generally a good idea to run GParted from a LiveCD.

---

