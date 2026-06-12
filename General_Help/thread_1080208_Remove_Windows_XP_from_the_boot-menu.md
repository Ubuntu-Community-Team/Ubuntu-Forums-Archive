---
title: "Remove Windows XP from the boot-menu"
date: 2009-02-25
forum: General Help
---

### Post by upapilot on 2009-02-25
How do i remove Windows XP from the GRUB menu?
Thanks in advance.:lolflag:

---

### Post by Joeb454 on 2009-02-25
```
gksudo gedit /boot/grub/menu.lst
```

Scroll down until you find the Windows XP entry, and either delete it, or comment it out by putting a # at the start of the lines :)

---

