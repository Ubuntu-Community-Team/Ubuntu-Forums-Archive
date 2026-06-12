---
title: "Prevent apache and mysql to start on boot"
date: 2009-04-19
forum: General Help
---

### Post by johannes_h on 2009-04-19
How do I prevent apache and mysql to start on boot?

Thanks

---

### Post by Iowan on 2009-04-19
I tend to do it the hard way - editing /etc/rcX.d files (rename with lowercase "s"). You didn't mention if your machine is CLI-only, but if Gnome-based, check System>Preferences>Sessions>Startup Programs - in case it's as easy as unchecking a box...

---

### Post by johannes_h on 2009-04-19
Thanks :D

---

