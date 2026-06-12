---
title: "Changing linux drive from slave to master..."
date: 2006-01-04
forum: General Help
---

### Post by sammydee on 2006-01-04
Right, here's my situation:

I'll call primary drives A, and master drives 1, so primary slave is A2, secondary master B1 etc.
I have a 4GB (yes I know) drive as A1. That has windows XP on, along with GRUB bootloader which went on when I installed ubuntu. I have a 40GB disk as A2, partitioned as 10GB linux and 30GB FAT32 storage. I got a new 80GB hard disk yesterday, and I eventually want to chuck out the old 4GB hard disk, and put a 10GB windows partition on the 40GB disk... Anyway it will eventually look like this:

40GB: 30GB linux, 10GB windows.
80GB: Fat32 storage space.

I don't mind reinstalling all the windows XP stuff, but I'd like to keep linux the way it is, or at least keep all my debian packages, accompanying config files, and home folder data stored so it is essentially the same as it is now. (I still can't decide whether I like gnome or KDE more - I have resorted to using the gnome desktop, but KDE applications.)

Anyway, the problem is, when I remove my 4GB disk, the GRUB goes with it and linux won't load. So either:

a) I need a way of backing up all my preferences, debian packages, config files and data in the home folder, then re-installing ubuntu to a new partition.
b) I resize the linux partition, put GRUB on the right disk (A1), and make sure it recognises ubuntu and XP ok.

Any ideas?

Thanks, Sam

---

### Post by sciurus on 2006-01-04
So right now you have a 4 GB master with Grub+Windows and a 40 GB slave with Ubuntu+Storage? The only clear-cut solution I see is to install the 80 GB for storage as master, resize the slave partitions using a live cd, install windows to the slave, then use the ubuntu cd to reinstall grub to either drive.

---

### Post by dcstar on 2006-01-05
[QUOTE=sammydee]
........
a) I need a way of backing up all my preferences, debian packages, config files and data in the home folder, then re-installing ubuntu to a new partition.
b) I resize the linux partition, put GRUB on the right disk (A1), and make sure it recognises ubuntu and XP ok.

Any ideas?

Thanks, Sam[/QUOTE]
I have seen a solution for this somewhere in the forums ages ago, Ubuntu "hard codes" some files when you install - in your case they will say "/dev/hdb" as the original Slave drive (on the first IDE channel), these have to be manually changed to "/dev/hda" and then Ubuntu should start up again as the first Master drive.

Do a search with some of your problem terms (like "change Ubuntu hard drive") and something useful should pop up.

---

### Post by Lyle on 2006-01-05
Have a look at the follwowing.

[http://www.ubuntuforums.org/showthread.php?t=35087&page=1](http://www.ubuntuforums.org/showthread.php?t=35087&page=1)
[http://www.ubuntuforums.org/showthread.php?t=106421](http://www.ubuntuforums.org/showthread.php?t=106421)

---

