---
title: "Hard drive recognition"
date: 2010-05-28
forum: Desktop Environments
---

### Post by nick6196 on 2010-05-28
I am running Ubuntu 10.04 LTS as a dual boot with WinXP but I am having problems with drive recognition in Ubuntu. I have four internal hard drives, 1 and 2 are standard master and slave and 3 & 4 are on a RAID card. Windows recognises them all okay every time but I have found through a lot of trial and error that Ubuntu will sometimes mount the drives in the order 1,2,3,4 and sometimes it will mount them in the order 3,4,1,2. No matter how I arrange the fstab file, it only works some of the time. If I load my music library into Banshee when the drives are mounted 1,2,3,4 then the next time I boot, if they are mounted 3,4,1,2 it can no longer find my music library etc...

Is there a way to make Ubuntu recognise the drives in the same order every time? Many thanks.

---

### Post by captain_171 on 2010-05-28
Take a peek at this.

[[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) ]("http://ubuntuforums.org/archive/index.php/t-793212.html")

---

### Post by nick6196 on 2010-05-28
This looks like exactly what I need. Many thanks!

---

### Post by nick6196 on 2010-05-28
Yes, using UUIDs in the fstab file has fixed the problem. The disks and all partitions mount perfectly now. Thank you for the link...that was driving me nuts!

---

