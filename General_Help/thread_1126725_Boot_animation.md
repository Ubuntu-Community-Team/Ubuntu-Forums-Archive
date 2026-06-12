---
title: "Boot animation"
date: 2009-04-15
forum: General Help
---

### Post by andy71600 on 2009-04-15
Is there any way to get rid of the boot animation and replace it with the scrolling console? I've been looking around without much luck.

Thanks

---

### Post by taurus on 2009-04-15
Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove **quiet splash** at the end of an entry for kernel.

Save it and reboot.

---

### Post by andy71600 on 2009-04-15
> **taurus said:**
> Edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove **quiet splash** at the end of an entry for kernel.

Save it and reboot.

Thanks, that worked like a charm... How about on shutdown?

---

### Post by taurus on 2009-04-15
It's going to be text too.  Try it.

---

