---
title: "Toggle icons on desktop to display or not"
date: 2009-08-28
forum: Desktop Environments
---

### Post by echo6 on 2009-08-28
I can use gconftool-2 -s /apps/nautilus/preferences/show_desktop --type boolean "false" to hide icons on the desktop.

However if I revert by using
gconftool-2 -s /apps/nautilus/preferences/show_desktop --type boolean "true"

The icons will not display until I log out and back in again, is there a way of toggling icon display on and off without having to log out and in ?

---

