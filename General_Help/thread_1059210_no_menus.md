---
title: "no menus"
date: 2009-02-03
forum: General Help
---

### Post by ledererster on 2009-02-03
I changed some graphics options, and now when I boot my computer up and log in, only the desktop shortcuts come up. No menu on top or taskbar. How can I fix this?

I'm using ubuntu 8.10.
Thanks!

---

### Post by UbuntuNerd on 2009-02-03
type this commands in a terminal: Applications > Accessories > Terminal
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
you should get all your panels back the same way they were.

---

### Post by Crafty Kisses on 2009-02-03
Are these the GNOME panels we're talking about, or programs?

---

### Post by UbuntuNerd on 2009-02-03
GNOME panels

---

