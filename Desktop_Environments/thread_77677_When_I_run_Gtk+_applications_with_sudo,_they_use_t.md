---
title: "When I run Gtk+ applications with sudo, they use the oooold standard Gnome theme"
date: 2005-10-17
forum: Desktop Environments
---

### Post by mostwanted on 2005-10-17
How do I fix something like that?

Examples: when I run synaptic or when I need to sudo gedit something (say /etc/fstab).

I had the same problem in Hoary. I think the problem showed up after changing themes a couple of times.

---

### Post by kaput on 2005-10-17
It's most likely because your current theme is in .themes in your home folder. In order for root-run apps to use your theme, try copying the theme's folder to /usr/share/themes/.

---

### Post by mostwanted on 2005-10-17
Thanks, that worked brilliantly!

---

