---
title: "Subpixel hinting? And why so many dependencies for Synaptic?"
date: 2008-05-19
forum: Debian
---

### Post by miggols99 on 2008-05-19
I recently installed Debian testing, and for the most part it's working fine. I just can't stand the ugly fonts! I need subpixel hinting otherwise the fonts kill my eyes. Also I tried to install Synaptic, but it dragged in loads of Gnome dependencies! When I tried sidux, it required hardly anything, but for some reason it wants a big chunk of Gnome. Can anyone help me with these problems?

---

### Post by pelle.k on 2008-05-19
I think you need a patched libfreetype6 for sub pixel hinting in kde. It's not included because of some patent/ip issues i belive.

---

### Post by kellemes on 2008-05-20
> **miggols99 said:**
> Also I tried to install Synaptic, but it dragged in loads of Gnome dependencies! When I tried sidux, it required hardly anything, but for some reason it wants a big chunk of Gnome.

Sidux probably already had these dependencies installed.

---

### Post by benuski on 2008-05-21
To change your font setting, go to the terminal, and then as root type "dpkg-reconfigure fontconfig-config".  You'll then be presented with three different options to configure.  I always go for "autohinter"(font tuning method) "always"(subpixel rendering) and "no, no, a thousand times no"(for bitmapped fonts).

---

