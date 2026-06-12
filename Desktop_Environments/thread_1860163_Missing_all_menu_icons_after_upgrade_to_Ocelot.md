---
title: "Missing all menu icons after upgrade to Ocelot"
date: 2011-10-14
forum: Desktop Environments
---

### Post by franapoli on 2011-10-14
I'm aware of the gconf "menu-have-icons" thing: already checked, it's ok, but still I can't see any icon in any context menu in Gnome. Any ideas where to look?

thank you

---

### Post by crdlb on 2011-10-14
The setting has moved from gconf to dconf. You can find it in gnome-tweak-tool in Theme, or in dconf-editor at org.gnome.desktop.interface.

---

### Post by franapoli on 2011-10-17
> **crdlb said:**
> The setting has moved from gconf to dconf. You can find it in gnome-tweak-tool in Theme, or in dconf-editor at org.gnome.desktop.interface.

Thank you very much, this solved my issue.

Anyway it's quite strange to me that on one hand I still have gconf-editor and I can use it to change attribute values (with no effect) and on the other hand I had to "apt-get install" dconf-editor, which is actually working.

Also, I have no gnome-tweak-tool (I'm installing it right now). Was it supposed to be installed on upgrade?

Just curiosities, but essentially thank you :).

---

