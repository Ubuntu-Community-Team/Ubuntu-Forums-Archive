---
title: "MBR Hijacked"
date: 2006-09-23
forum: Desktop Environments
---

### Post by alecjw on 2006-09-23
I've just reinstalled windoze again; so, of cource, it's hijacked my MBR (so no GRUB!)
last time this happened, I was told to do this:
```
sudo grub
find /boot/grub/stage1
root <output of above command>
setup hd0
quit
```
and it worked. But this time, it didn't. When i typed in setup hd0, it said error 11, invalid device name string. How do I fix this?


Edit: Problem solved. It shou8ld have been setup (hd0), not setup hd0.

---

### Post by colo on 2006-09-23
The syntax of the GRUB-shell requires you to but brackets around arguments of commands, like "setup (hd0)", for example.

---

