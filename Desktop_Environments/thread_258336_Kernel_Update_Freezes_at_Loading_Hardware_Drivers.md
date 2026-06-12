---
title: "Kernel Update Freezes at Loading Hardware Drivers"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Paul Gilster on 2006-09-15
The problem with my system freezing at "Loading Hardware Drivers," which has been the case ever since the upgrade to Dapper, persists with the latest kernel. The only way I have found to fix it is to remove the 'quiet splash' options for the kernel in the /boot/grub/menu.lst file. I don't know understand Linux well enough to know why the splash option freezes my system at "Loading Hardware Drivers," but it's clear that it's the culprit. I gather that few are still having this problem (at least, my posts about it here have brought no responses), but for those who do, it's something I hope the next kernel can fix.

---

