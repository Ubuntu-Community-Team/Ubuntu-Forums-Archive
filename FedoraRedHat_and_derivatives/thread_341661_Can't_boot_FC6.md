---
title: "Can't boot FC6"
date: 2007-01-18
forum: Fedora/RedHat and derivatives
---

### Post by macogw on 2007-01-18
I have Edgy on my internal hard drive, and then I have an external that I use to mess around.  It has 3 partitions + swap.  The first partition is Feisty, and the second is FC6, the third will have Sabayon.  The install seemed to go fine, but now it won't boot Fedora!  The two Ubuntu installs are fine (not that Feisty works fine, but that's to be expected).  For Fedora, I edited GRUB (didn't let it do it itself because it would've messed up my Ubuntu boot entries, or at least I feared it would), and it goes to Starting up... and all that.  Then it gets to:
usb: 1-1 device not accepting address 2; error -71
sda: assuming drive cache: attempting write through
sda: assuming drive cache: attempting write through

then stuff about how it can't move /dev/root and cant mount /proc and /dev and then
Kernel panic - not syncing: attempting to kill init!

Does anyone know what's going wrong or how to fix this?

---

