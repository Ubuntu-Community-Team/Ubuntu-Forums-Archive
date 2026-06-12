---
title: "totem-xine wanting to remove ubuntu-desktop"
date: 2006-05-14
forum: Desktop Environments
---

### Post by DarkStarDeity on 2006-05-14
Last night I installed totem-xine through synaptic and it wanted to remove ubuntu-desktop. I let it, but after reading some threads and stuff on the wiki, I got nervous and tried to re-install ubuntu-desktop - but it wants to remove totem-xine to do it. What gives? Is this going to mess up my system and if so, how can I install totem-xine without messing it up?

---

### Post by endersshadow on 2006-05-14
ubuntu-desktop is just a meta package that creates dependencies.  Leave it with totem-xine installed and ubuntu-desktop uninstalled :)

---

### Post by DarkStarDeity on 2006-05-14
Without the meta-package to "co-ordinate" things, will leaving it like this leave me in update-dependency-hell, where updating one package won't automatically check for updates for other dependant packages?

---

### Post by endersshadow on 2006-05-14
[QUOTE=DarkStarDeity]Without the meta-package to "co-ordinate" things, will leaving it like this leave me in update-dependency-hell, where updating one package won't automatically check for updates for other dependant packages?[/QUOTE]

No.  Nothing is dependent on ubuntu-desktop, ubuntu-desktop just has its own dependencies.  The metapackage makes it easy to install various desktop environments (such as kubuntu-desktop).  Every other package is marked with its specific dependencies, so you can rest assured that your system will stay up-to-date just fine.  This is Debian based, after all, not Fedora based :-D

---

### Post by DarkStarDeity on 2006-05-14
Thanks for the reassurance.

---

