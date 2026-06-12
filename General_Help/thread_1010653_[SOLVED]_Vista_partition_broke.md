---
title: "[SOLVED] Vista partition broke"
date: 2008-12-14
forum: General Help
---

### Post by magmon on 2008-12-14
And, I would love to remove it and the option to boot to it. Removing it is easy enough, but is there a way to get rid of the option? I just want it to go strait to ubuntu, no "select the os" screen.

---

### Post by taurus on 2008-12-14
You can modify /boot/grub/menu.lst.  You can change the _timeout_ to whatever seconds you want.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by magmon on 2008-12-14
Sweet, should I first remove the partition or run that command first?

---

### Post by taurus on 2008-12-14
Doesn't matter.  What are you going to do with the windows partition, ntfs, after you remove windows?

---

### Post by magmon on 2008-12-14
Im going to give the space to ubuntu.

---

