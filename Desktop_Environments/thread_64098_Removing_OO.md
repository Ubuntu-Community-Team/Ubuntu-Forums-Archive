---
title: "Removing OO"
date: 2005-09-09
forum: Desktop Environments
---

### Post by chscag on 2005-09-09
In the process of removing Open Office (never use it) via Synaptic, the removal message states that it's going to remove the Desktop along with OO.   [-X   I figure something is not right here.  Anyone know why in the world it wants to remove the desktop along with OO?  Thanks.

---

### Post by cwaldbieser on 2005-09-09
[QUOTE=chscag]In the process of removing Open Office (never use it) via Synaptic, the removal message states that it's going to remove the Desktop along with OO.   [-X   I figure something is not right here.  Anyone know why in the world it wants to remove the desktop along with OO?  Thanks.[/QUOTE]

Some packages like "ubuntu-desktop" are just groupings for all the component packages so you don't have to install them all individually.  OO was one of these, core packages, so when you remove it, you have broken the group.  However, it's not going to really uninstall all the other pieces associated with the desktop.

This type of package is often referred to as a meta-package.

---

