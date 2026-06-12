---
title: "Cannot see USB Memory Stick"
date: 2009-05-11
forum: General Help
---

### Post by stevebond001 on 2009-05-11
Hi
I have recently upgraded to Jaunty and now whenever I plug in a memory stick, nothing happens.  The drive does not auto open on my desktop, I can't browse to it, nothing...

All was well under Hardy, the memory sticks loaded and opened without any problem.  I've also tried different USB devices as well, nothing seems to load.

Has anybody got any ideas?

Many thanks in advance

---

### Post by pro003 on 2009-05-11
type in terminal:

```
sudo mount -a
```

and then

```
fdisk -l
```

your usb device should be seen as **sdb1**

---

### Post by stevebond001 on 2009-05-11
Hi
Thanks for the advice - Tried what you suggested but still can't access the device. Any further help would be appreciated.

---

### Post by stevebond001 on 2009-05-11
Update.
After trying the commands listed previously, I have rebooted and everything now works OK.  Hopefully this will help somebody else.

---

