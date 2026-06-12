---
title: "Force password asking"
date: 2006-06-19
forum: Desktop Environments
---

### Post by viraptor on 2006-06-19
Now something completely different...
How can I force asking for password when coming out of sleep (suspend to mem)? Now, I get desktop just after opening the lid. I'd like to have a login screen, like after the screensaver. I tried to look in /etc/acpi/* scripts, but haven't found anything related there.

---

### Post by FuturePast on 2006-06-19
Run gconf-editor from a terminal, and then change the key /apps/gnome-power-manager/lock_on_suspend to True.

---

### Post by viraptor on 2006-06-19
Thank you very much :)
Now it's just great!

---

