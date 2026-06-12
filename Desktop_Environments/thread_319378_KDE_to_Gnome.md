---
title: "KDE to Gnome"
date: 2006-12-15
forum: Desktop Environments
---

### Post by dontgetshocked on 2006-12-15
I installed from gnome to kde thru terminal.
Now, I need to go back to my original gnome desktop if I can

What code do I need ?

---

### Post by d3v1ant_0n3 on 2006-12-15
If you didn't remove gnome when you installed KDE, just switch sessions at the login screen- there should be a popup menu which allows you to do this- just select GNOME and login.

If you *did* remove gnome, enter this into terminal:

```
sudo aptitude install ubuntu-desktop
```

---

