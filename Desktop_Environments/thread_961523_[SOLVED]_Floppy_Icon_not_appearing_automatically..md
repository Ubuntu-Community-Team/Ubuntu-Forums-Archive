---
title: "[SOLVED] Floppy Icon not appearing automatically."
date: 2008-10-28
forum: Desktop Environments
---

### Post by alexham on 2008-10-28
Hi,Guys,

When I insert a CD/Dvd into the drive an icon appears automatically on the desktop and clicking on it opens up the contents. But nothing happens when I insert a floppy.

I can read the contents by going to Places>Removable Media, so this is not a problem, but I would like to get the floppy to appear automatically.

I Mepis that would involve adding a line to /fstab, but I know little of Ubuntu architecture and would need assistance to do it.

Many thanks,

Alex

---

### Post by Tamlynmac on 2008-10-28
check:
gconf-editor/apps/nautilus
Are the "media_automount" and "media_automount open" boxes checked?

---

### Post by maybeway36 on 2008-10-28
Floppy drives are completely mechanical, and so the OS has no way of knowing you've put a floppy disk in until you try to access it.

---

### Post by alexham on 2008-10-28
> **Tamlynmac said:**
> check:
gconf-editor/apps/nautilus
Are the "media_automount" and "media_automount open" boxes checked?
They are both checked, thanks.

alex

---

