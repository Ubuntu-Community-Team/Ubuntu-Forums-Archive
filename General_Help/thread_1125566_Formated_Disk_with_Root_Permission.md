---
title: "Formated Disk with Root Permission"
date: 2009-04-14
forum: General Help
---

### Post by lvalen18 on 2009-04-14
I been having this problem... Every time i format my Secondary Disk i don't have permission to write or access it as a normal user but i can only access it and write by "**Sudo Nautilus**"..:mad:. How do i format Disk BUT still be able to Read/write to it as a normal user.. I don't want to keep it as a FAt or NTFS disk

---

### Post by bluefrog on 2009-04-14
change the permissions of the mount point

---

### Post by Penguin Guy on 2009-04-14
I believe this is an error - fat16 does not support Linux permissions so it seems to assign fat16 filesytems random permissions.

---

### Post by lvalen18 on 2009-04-14
> **bluefrog said:**
> change the permissions of the mount point

I don't kno how to change the Mount point permissions...When i format a USB with Gnome Partition Editor it goes okay.. I guess since its a USB there aren't no permissions.

---

