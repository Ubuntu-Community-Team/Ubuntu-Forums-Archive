---
title: "ubuntu not starting:kernel panic"
date: 2005-12-09
forum: Desktop Environments
---

### Post by mabuti on 2005-12-09
I installed Ubuntu on my PC a few months ago, recently when I boot
Ubuntu it gives me the following message:
Starting...
pivot_root: No such file or directory
/sbin/init: 429: cannot open dev/console: No such file
Kernel panic: Attemted to kill init!

How to fix this problem,...do I have 2 re-install Ubuntu?
Help!

---

### Post by blueplazma on 2005-12-09
You shouldn't have to reinstall.  Try getting an install CD and boot off of it.  When you're given the option to give arguments before booting, type 'rescue'.  The CD will give you a root shell.  From there you should try reinstalling your kernel image.

---

### Post by mabuti on 2005-12-09
How to install the "kernel image"?

---

