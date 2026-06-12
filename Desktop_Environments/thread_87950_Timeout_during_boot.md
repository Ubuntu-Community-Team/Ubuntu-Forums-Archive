---
title: "Timeout during boot"
date: 2005-11-09
forum: Desktop Environments
---

### Post by cerberos on 2005-11-09
Just after the "Loading Linux" prompt my boot process pauses for 30seconds to eventualy display:
Ata2 failed to respond (30 secs)
which is fairly anoying, I can't seam to work out where I can tell linux to stop trying to initilise it.

This started to appear just after I unplugged several hard drives from multiple controllers, now i just have 1 sata drive on the onboard sata controller and 1 DVD burner on the ata controller.

---

### Post by 23meg on 2005-11-09
See if you have an ata2 entry in your /etc/modules.

---

### Post by cerberos on 2005-11-09
/etc/modules is:
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

amd74xx
sd_mod
sr_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
sbp2
lp
fglrx

---

