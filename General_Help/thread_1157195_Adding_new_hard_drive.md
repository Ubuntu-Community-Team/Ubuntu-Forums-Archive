---
title: "Adding new hard drive"
date: 2009-05-12
forum: General Help
---

### Post by Nighthawk4900 on 2009-05-12
I recently got a new hard drive and want to have both windows xp and ubuntu available to me.

currently i have a 320gb hard drive with three partitions: ntfs, ext3, and the linux swap.

the ntfs is from when I had XP as my main os. after installing ubuntu8.10, i managed to royally mess up the boot stuff and windows became inaccessible. But all my data is still accessible through ubuntu, so i decided not to mess around with it anymore in case I totally mess up and lose all my data. 

now i just purchased a new 500gb hd in order to properly save my work and need suggestions on how to do this properly. 

my goal is to finally have 2 partitions on each hard drive. 
hdd1: [Windows XP] [my data]
hdd2: [Ubuntu] [copy of data from hd1][swap]

one partition on each drive will be the operating system. then the second partition will be my "data" which will be the same on both drives (redundancy for data security). Ill just use norton ghost to periodically copy the data partition from disk1 to disk2.


both my HDDs are SATA drives

please advise me on how to start and what to do. I need to end up being able to properly boot up both windows and Linux, as well as have access to all my data that i currently have...

thanks!

---

### Post by logos34 on 2009-05-12
Either copy xp to the new disk using [Gparted]("http://gparted.sourceforge.net/larry/move/move.htm"), and try to fix it there (fixboot, fixmbr, running chkdsk, etc.) or else reinstall it.

You probably already have [fs-driver]("http://www.fs-driver.org/index.html") installed, so no need to tell you about that.

Add an xp boot entry to grub menu [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Boot the ubuntu live cd and use gparted to delete old xp partition, and grow ubuntu / to the left to incorporate the space.

---

