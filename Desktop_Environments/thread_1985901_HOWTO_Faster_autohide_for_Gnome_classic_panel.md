---
title: "HOWTO Faster autohide for Gnome classic panel"
date: 2012-05-24
forum: Desktop Environments
---

### Post by nathan726 on 2012-05-24
Here's how to set up Gnome Panel to auto hide instantly without animations or delays...

First open dconf-editor and navigate to /org/gnome/desktop/interface and uncheck the enable-animations key.

Then go to /org/gnome/gnome-panel/layout/top-levels/top-panel (or similar) and ensure that auto-hide is checked, hide-delay is set to 0 and unhide-delay to set to 0.

---

### Post by ktmom on 2012-07-12
Thank you!

---

### Post by honklinux on 2012-11-19
Thank you!!!

---

