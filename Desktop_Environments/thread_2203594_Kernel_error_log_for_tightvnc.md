---
title: "Kernel error log for tightvnc"
date: 2014-02-04
forum: Desktop Environments
---

### Post by gopukrishnan on 2014-02-04
Hi,

My Vnc connection stops working when I do something related with GUI (open firefox,package manager etc). Following logs I found from kern.log :


Feb  4 13:19:04 server1 kernel: Xtightvnc[11184]: segfault at 7fffacd91000 ip 0000000000449dd0 sp 00007fffacd8fe90 error 6 in Xtightvnc[400000+17c000]
Feb  4 13:19:04 server1 kernel: grsec: From 116.203.157.245: Segmentation fault occurred at 00007fffacd91000 in /usr/bin/Xtightvnc[Xtightvnc:11184] uid/euid:1000/1000 gid/egid:100/100, parent /sbin/init[init:1] uid/euid:0/0 gid/egid:0/0

---

