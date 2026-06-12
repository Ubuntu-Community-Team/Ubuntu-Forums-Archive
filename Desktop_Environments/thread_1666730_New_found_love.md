---
title: "New found love"
date: 2011-01-14
forum: Desktop Environments
---

### Post by Pipedreams on 2011-01-14
I recently converted from windows to Linux 3 months ago, I admit at first it was hard to get a handle on it but the more I figured it out the less I booted windows 7 until yesterday i need it for a friend and then it dawned on me, I hate it and it's just taking up valuable space i could be using enjoying my laptop instead of just looking at it spin! These forums are life support and I truly thank everyone that has helped me along the way with my issues in figuring things out. Super helpful, tentative, and patient. I as if I've never used a computer until now.

---

### Post by bobcollard on 2011-01-14
The simplest solution should not be over your head if you have a few simple pieces of equipment.  You need to make a backup of the visible files in your Home directory.   You can do this on a CD, a DVD, a USB Flash drive or an external HD.  Then reinstall your Linux distribution and check "Use Entire Disk" instead of "Install Side by Side" when it comes to the question for partitioning.  Then simply copy your home backup to the new home directory.
The hard way if you don't know something about partitioning is to use Gparted and erase the partition for Windows and stretch your current partition to take it into account.  While the second way is easier, if you know what you are doing, you still should keep a backup of your Home directory.  After that you need to open terminal and run:
sudo update-grub
It will ask for your password and will not show it while you type it, then hit Enter.

---

