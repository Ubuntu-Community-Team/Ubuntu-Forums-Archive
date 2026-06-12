---
title: "Problems with package install/remove and menu items"
date: 2008-12-07
forum: General Help
---

### Post by samjh on 2008-12-07
Why is it that sometimes when a package is uninstalled (ie. via aptitude, apt-get, or synaptic), its Gnome menu items are not removed; and when the items are removed manually (ie. via Alacarte or manual removal of the desktop and directory files) and the software reinstalled, the menu items are not created (I don't mean they're hidden, but they aren't created at all)?

For example:
1. Install FlightGear
2. Remove FlightGear (remove or purge, it doesn't matter)
3. Gnome menu item will remain in place even after relogin or reboot.  So remove manually via Alarcarte or by deleting the .desktop file.
4. Reinstall FlightGear.
5. No item in Gnome menu at all.

How do I fix this problem?

PS: This doesn't happen with everything, only some packages.  GVim is another one with this problem.  Wine is especially trouble-some, as it creates its own directory structure and makes menu items and directories for software installed via the layer.

---

