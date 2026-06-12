---
title: "Removing VMware service"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Gannin on 2006-08-29
The other day I installed VMware Player to try out a few VMware images.  When I was done, I tried uninstalling it using the uninstallation script it provided.  It left behind a few directories which I manually deleted, and I made sure /etc/init.d/ was clean.  I restarted my computer to make sure the kernel modules were completely out of memory.

The problem is, when I look at the various services for my system (I use sysv-rc-conf) vmware is still listed as an available service.  I've gone into /etc and done a "find . | grep "vmware"" and I've also done a "grep -R "vmware" *" and neither one produced anything.  Does anyone have any idea what I may be missing?

---

