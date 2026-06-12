---
title: "missing system tray"
date: 2009-06-16
forum: General Help
---

### Post by 2roombas on 2009-06-16
I foolishly removed all of the icons from my top panel and bow get this message every time I load.  How can I get that back?

---

### Post by 3rdalbum on 2009-06-16
Add a Notification Area applet to one of your panels. HPLIP is complaining that you don't have one and therefore it can't display its icon.

---

### Post by ZackM on 2009-06-16
Maybe resetting the panel to default settings would help as well?

```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel
```

---

### Post by 2roombas on 2009-06-16
> **3rdalbum said:**
> Add a Notification Area applet to one of your panels. HPLIP is complaining that you don't have one and therefore it can't display its icon.

\Thank you.  That was easy! :)

---

