---
title: "Low Disk Space (Ubuntu 12.04)"
date: 2012-09-30
forum: Desktop Environments
---

### Post by GouthamGMV on 2012-09-30
Hey,

Since I'm constantly getting low disk space notifications and I'm having to do "sudo apt-get clean" almost every day, I decided I'd ask you guys for help.

I've installed Ubuntu 12.04 using the Windows Installer on a separate partition of around ~15 GB.

The thing, my home folder has only 62 MB left after the clean thing, while I see several filesystems like /dev, /run and /host taking up LOADS of empty space. Is there any chance I could allocate all these space to my home folder? I can't install ANYTHING now, due to the low disk space. Here's a screenshot of my "df -h" result. Hoping you guys could help me out. Thanks! :)

[IMG]http://i45.tinypic.com/2gtvq1l.png[/IMG]

---

### Post by zombifier25 on 2012-09-30
I doubt that 15GB will cut it for Ubuntu. Yes, Ubuntu will run, but you'll need a bit more than that.

I can't directly answer your question, but you can search for more junk files and clean them using BleachBit. Install it, use it (both as normal user and as root) and see if it helps.

```
sudo apt-get install bleachbit
```

---

### Post by jerrrys on 2012-09-30
+1 for BleachBit, but looks like your HDD is tapped out.  Time for a new one?

---

