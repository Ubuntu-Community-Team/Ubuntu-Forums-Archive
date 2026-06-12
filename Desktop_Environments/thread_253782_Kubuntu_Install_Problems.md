---
title: "Kubuntu Install Problems"
date: 2006-09-08
forum: Desktop Environments
---

### Post by leetcharmer on 2006-09-08
I have an hp pavilion ze4600; everytime I boot to the Kubuntu/Ubuntu liveCDs and try to install, I get problems when it comes time to resize partitions.  I want to keep resize the ntfs partition and devote 10GB for Ubuntu/Kubuntu.  Everytime it tries to resize, it gets an input/output error and then filesystem checks fail so -- it's unable to complete the operation.  When I reboot to windows, it does the scandisk, and everything goes back to normal on that end.

How do I get passed that and resize the partition?  Should I upgrade to SP2 first?  Should I defrag?  Any suggestions?

---

### Post by divague on 2006-09-08
You could try using partition magic to resize the partition

---

### Post by leetcharmer on 2006-09-08
:/ did they release a free / open source version of partition magic  yet?

---

### Post by leetcharmer on 2006-09-09
I burned a liveCD of GParted and it claimed that there were input/output errors.  It ran the simulation of resizing the ntfs partition, and that ran fine -- but when it actually tried, it failed.

It said that it thought the hard drive may be deteriorating, so -- I ran a chkdsk /f /r twice and did a defrag.

Problems are still there, and it won't even let me try to resize now.  Any ideas how I can resize this partition?  Perhaps I need to buy a new laptop hdd :/.  Thoughts?[-o<

---

