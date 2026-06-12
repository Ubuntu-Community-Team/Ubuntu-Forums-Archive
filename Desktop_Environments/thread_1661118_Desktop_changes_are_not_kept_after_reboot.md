---
title: "Desktop changes are not kept after reboot"
date: 2011-01-06
forum: Desktop Environments
---

### Post by Jonners59 on 2011-01-06
I have a PC running 10.10 Gnome 2.32.0 Kernal 2.6.35-24-generic-pae, i686

I am using /dev/sda3 on my primary hard drive (200Gb) to run my Kernal
I have all my documents stored on a second, 500Gb hard drive: sdb2

I have noticed in the past 2 days that I delete or move files and folders, but when I reboot they re-appear.  I have ALSO noticed today that the Templates folder within my Documents folder, I have a copy of my /etc/ directory....  God only knows how that got there!  It is a copy and I am wondering:

a.  How it got there
b. Could it be the cause of the problems
c. How I remove it.

---

### Post by Jonners59 on 2011-01-06
Solved:
It would seem that the Backup I created - I use "Lucky Backup" which was on a separate Partition (sdb1) was causing the problem, or so it would appear.

I found a number of directories, some empty in other places, and every time I deleted them when I rebooted they reappeared.

So I deleted the back up and these directories/copies and rebooted, problem gone away.  I also removed the auto mount for the Backup partition.

So far all seems to work fine.

---

