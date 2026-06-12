---
title: "Problems with fglrx and drm"
date: 2006-09-17
forum: Desktop Environments
---

### Post by phork on 2006-09-17
I am having problems getting the fglrx and drm modules loaded at the same time into the newest kernel.  If drm is loaded first:
(root@obsidian:~)# modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.15-26-686/kernel/drivers/char/drm/fglrx.ko): Operation not permitted

If fglrx is loaded first....
(root@obsidian:~)# modprobe drm
FATAL: Error inserting drm (/lib/modules/2.6.15-26-686/kernel/drivers/char/drm/drm.ko): Out of memory

Any ideas?

---

### Post by phork on 2006-09-17
Sorry, the fglrx then drm error was from memory.  The exact error is:
(root@obsidian:~)# modprobe drm
FATAL: Error inserting drm (/lib/modules/2.6.15-26-686/kernel/drivers/char/drm/drm.ko): Cannot allocate memory

---

