---
title: "[SOLVED] qtconfig/keepass segmentation fault"
date: 2008-06-14
forum: Desktop Environments
---

### Post by brazilla ray on 2008-06-14
Hi there- I recently reinstalled Ubuntu after trying out Kubuntu for awhile, and having a separate /home partition, all my settings for qt applications were preserved (the main one in question was keepassx).  Trying to find a quick and easy way of reverting to some kind of default, I tried deleting the Trolltech.conf file from ~/.config.  Now when I try to run qtconfig or keepass from the terminal, I get : Segmentation fault.  Anyone have any thoughts?

---

### Post by brazilla ray on 2008-06-15
Well- after thoroughly purging all qt related packages, rebooting in recovery mode, and then reinstalling qt4-qtconfig and dependencies, everything works now.

---

