---
title: "Disk Space on Root Partition Being Taken By Something"
date: 2011-08-22
forum: Desktop Environments
---

### Post by krisdotca on 2011-08-22
I have a Ubuntu Desktop 10.10 x32 installation and something is slowly (or rather quickly actually) consuming all of the disk space on the root partition. I've lost ~40MB in the last 30 minutes and I can't figure out where it's going.

I've been using df -H to monitor the available space. During the same time, I've been doing a "du -s -m *" on the root partition to see what's increasing but there's nothing that's gotten noticeably bigger.

Can anyone offer any suggestions on how I can determine where all the space is going?

Thanks!

---

### Post by 3Miro on 2011-08-22
Look at the folders /tmp and /var/tmp. Are those growing?

---

### Post by Frogs Hair on 2011-08-22
Check your log file viewer for possible problems . Open the disk Utility an check disk health by selecting smart data . That's downright weird !

---

### Post by Dngrsone on 2011-08-22
I've recently had problems with log files growing exponentially large until the system crashed and I couldn't even log into gnome.

Bleachbit worked well for me to clean out several GB of stuff.

---

### Post by krisdotca on 2011-08-22
Thank you to everyone who responded. I never managed to find what was consuming all of the disk space. We rebooted the system at the end of the day and it refused to start again so my best guess is some kind of disk corruption.

We finally managed to get it back online again by booting from the install CD and dropping to a root prompt to scan the hard disks.

Thanks again!

---

