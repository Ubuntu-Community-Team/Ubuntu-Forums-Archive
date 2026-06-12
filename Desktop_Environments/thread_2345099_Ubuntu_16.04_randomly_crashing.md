---
title: "Ubuntu 16.04 randomly crashing"
date: 2016-11-30
forum: Desktop Environments
---

### Post by John_Creane on 2016-11-30
I'm running Ubuntu 16.04, it's regularly patched with a cronjob scheduled once a week to carry out the patching & the reboot afterwards. 

For the first time I've had an Ubuntu Desktop crash on me, twice after I power cycled it.The mouse & keyboard were non responsive so I couldn't try any of the control alt combinations to restart it gracefully. 

I've got it running just now, ran the dist-upgrade & there was a kernel update available & it's installed but how do I find out what caused my problem earlier, is there a specific log I should be looking through before I start checking for hardware failures?

---

### Post by TheFu on 2016-12-01
All of them. Look for "warning" and "error".  After the crash and reboot, some files will be overwritten, so after the crash, boot off alternate media (like a flash drive), mount the partition with the log files and review them.  I'd use **egrep** to search them all, but there are 50 different ways to do the same thing.

BTW, I'd not use cron to run patches. Sometimes questions are asked and **need** to be answered correctly.  If you think using cron for patching is still needed, be certain to log everything and review those weekly for any issues.  Sometimes patching has problems and stuff in stdout and stderr are the best data about that.

---

