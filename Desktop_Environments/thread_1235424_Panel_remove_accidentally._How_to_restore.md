---
title: "Panel remove accidentally. How to restore?"
date: 2009-08-09
forum: Desktop Environments
---

### Post by CONCORAN on 2009-08-09
Hi,
I was trying to move some icons around on the top panel (one with applications, places, system etc menus), and accidentally removed the whole panel instead of one of the icons.
Can someone please tell how to restore it?

Thanks in advance.

Update: Earlier I had posted that I've found the answer, but it appears I was wrong.

---

### Post by arky on 2009-08-09
Remove gnome-panel from current session, unset and restart gnome-panel

gnome-session-remove gnome-panel

gconftool-2 --recursive-unset /apps/panel

gnome-panel &

---

