---
title: "Cannot configure menu / open applications menu"
date: 2009-05-17
forum: General Help
---

### Post by tigerhawkvok on 2009-05-17
So I have an Ubuntu Jaunty installation on an Eee PC, and I had run out of room.  After this happened, I cleared out as many files as possible (I couldn't even save text files) including /var/tmp and /tmp, autoclean, deborphan, localepurge, etc.  Some point along here lost my desktop customizations (not a big deal), but more importantly, I lost access to my Applications menu (I can click it, but it will not do anything, just turn blue briefly).  After this, I tried to configure the Main Menu from System (in case it had disabled everything in the App menu), but the configuration would not launch.  I tried following the instructions for that on this forum, to no avail, then tried to chmod ~/.config/menus to 0777, but neither of tehse worked either.  Any ideas?

Thanks!

---

### Post by mc4man on 2009-05-17
You could try something one of 2 ways
Either browse to ~/.config/menus and delete applications.menu or from terminal

To get terminal,  Alt+F2 ->  type in  -> gnome-terminal

```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak
```

---

### Post by tigerhawkvok on 2009-05-17
Thanks!  I thought just deleting it would get me into trouble.  This worked, though.

---

