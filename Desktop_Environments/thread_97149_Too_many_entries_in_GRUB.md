---
title: "Too many entries in GRUB"
date: 2005-11-30
forum: Desktop Environments
---

### Post by sirdeets on 2005-11-30
Every time I do a dist-upgrade and acquire a kernel package, a new entry is added to GRUB. I think I have something like 4-5 versions of Ubuntu listed there. How can I clear some of these superfluous entries?

---

### Post by teaker1s on 2005-11-30
safest way remove old kernels completely with synaptic-that's the way I do it and it automatically edits grub

---

### Post by Xian on 2005-11-30
If you want to save a backup kernel use option #1.
This is generally a good idea.

1. Open the menu.lst file with admin priveys:
$ sudo gedit /boot/grub/menu.lst

Comment out the entries you don't want visible at boot.

2. Use synaptic and remove the kernels you no longer need.
That should also remove the grub entries.

---

