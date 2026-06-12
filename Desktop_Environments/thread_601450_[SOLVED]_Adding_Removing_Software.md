---
title: "[SOLVED] Adding Removing Software"
date: 2007-11-03
forum: Desktop Environments
---

### Post by BigBlackYak on 2007-11-03
Hi.

I am new to Ubuntu. I think its pretty cool though. Started with Feisty Fawn and moved to Gutsy Gibbon. I keep getting this message when adding new applications E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I need to do to ensure this doesn't keep happening? I've restated my machine, powered down down and up again to no avail. Would appreciate any help. 

The Yak.

---

### Post by taurus on 2007-11-03
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by BigBlackYak on 2007-11-03
Thanks Taurus!

---

