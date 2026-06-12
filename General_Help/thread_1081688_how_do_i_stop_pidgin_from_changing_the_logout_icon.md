---
title: "how do i stop pidgin from changing the logout icon"
date: 2009-02-26
forum: General Help
---

### Post by default00 on 2009-02-26
Is there anyway I can stop pidgin from changing the logout icon from the normal icon to a pidgin icon (green circle for available, red triangle for away, etc)?

---

### Post by T.J. on 2009-02-27
I'm not entirely sure what you mean, but if you mean changing status automatically when not in use - that's under preferences-> status/idle.

---

### Post by edmicman on 2009-03-09
Did you ever figure this out?  I've been wondering, too.

The problem is not about the idle status changing...

After the last update (I think it came with 8.10?), your Pidgin status (away, available, etc.) displays to the right-hand side of your login name, on the top gnome toolbar.  This "status" icon replaces the normal gnome logout/restart/shutdown button.  

My Pidgin status is already displayed and controlled by Pidgin's toolbar icon; I don't want the separate status icon.  Is there a way to disable it?

---

### Post by kanikilu on 2009-03-09
Open a terminal (Applications > Accessories > Terminal) or press ALT+F2 and run

```
gconf-editor
```

Browse to /apps/fast-user-switch-applet and uncheck the box next to "show_presence_info".

---

