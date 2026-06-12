---
title: "Oneiric Ocelot cannot remove gnome-session fallback"
date: 2012-01-14
forum: Desktop Environments
---

### Post by test_tube_baby on 2012-01-14
Hello folks!

I am running Unity (Ubuntu 2D) desktop environment on Oneiric Ocelot however, I have the gnome panel over the unity panel.
How do I remove this gnome panel?

I've already tried apt-get remove gnome-session-fallback and from synaptic I removed all *appmenu* apps.

But still when I hover over to my Unity bar, the gnome panel comes up. I can't seem to get rid of it. Any ideas?

See screenshot attached.



Thanks!

---

### Post by Krytarik on 2012-01-14
First, check if Gnome Panel is listed in your "Startup Applications" and is enabled, also try removing the content of "~/.config/gnome-session/saved-session"; mainly to get your system in a clean state.

Then make sure all packages pulled in by "gnome-session-fallback" on its installation are removed as well:
```
sudo apt-get autoremove --purge
```And if you installed the Gnome Fallback sessions through another way, namely by installing "gnome-panel" instead of its package directly, as often weirdly suggested, or if the above command doesn't remove "gnome-panel", remove it directly:
```
sudo apt-get purge gnome-panel
sudo apt-get autoremove --purge
```Regards.

---

