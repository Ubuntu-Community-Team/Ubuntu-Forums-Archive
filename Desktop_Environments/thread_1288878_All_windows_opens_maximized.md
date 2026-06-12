---
title: "All windows opens maximized"
date: 2009-10-11
forum: Desktop Environments
---

### Post by doggystyle on 2009-10-11
I've just installed 9.04 netbook remix and disabled the netbook desktop view (since it lagged too much). However, every new window (not only Gtk) I open starts maximized, which is very annoying.

Any hidden setting i need to know about to disable this?

---

### Post by kerry_s on 2009-10-11
it's in gconf-editor under apps-> maximus

---

### Post by ugm6hr on 2009-10-12
Or just remove it:
```
sudo apt-get remove maximus
```

---

### Post by timmyhiggy on 2009-10-19
or you can add certain things to the exceptions list for maximus, as described here

[http://forum.eeeuser.com/viewtopic.php?id=53528](http://forum.eeeuser.com/viewtopic.php?id=53528)

that way you keep maximus running but don't end up having EVERY window maximised...

---

