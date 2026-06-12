---
title: "Nitrogen Restore"
date: 2011-01-23
forum: Desktop Environments
---

### Post by mooreted on 2011-01-23
Using OpenBox and Nitrogen for my wall paper. My autostart.sh is simple:

tint2&
pidgeon &
nitrogen --restore &

Nitrogen does indeed restore my desktop then the default Ubuntu desktop background comes up after that.

How can I stop the default Ubuntu wallpaper from loading after my Nitrogen wallpaper?

---

### Post by mooreted on 2011-01-23
Oops, light bulb went off after I posted, sorry.

Solution:

gnome-settings-daemon &
tint2 &
pidgin &
(sleep 3 && nitrogen --restore) &

---

