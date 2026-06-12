---
title: "Removing old kernel options from GRUB"
date: 2006-09-14
forum: Desktop Environments
---

### Post by max.diems on 2006-09-14
How do I remove options to boot into old kernels in GRUB?

---

### Post by mitch.c on 2006-09-14
Assuming the old kernels no longer exist in /boot...
```
sudo update-grub
```
See the man page for more info.

---

### Post by ronmarley1 on 2006-09-14
Go into synaptic and search for "kernal <rev.#>".  Remove the ones you don't want.  By the way, I keep the newest one and the one previous, just in case I need to revert for some reason (I've never actually had to, but I got the advice from another user, and it seemed prudent).

---

