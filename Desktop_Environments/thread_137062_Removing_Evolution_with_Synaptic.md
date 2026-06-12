---
title: "Removing Evolution with Synaptic"
date: 2006-02-27
forum: Desktop Environments
---

### Post by jimpa on 2006-02-27
Hi! 
Im a new user to ubuntu. (and linux)
Im running low on diskspace and want some more space, so i was thinking about removing some programs that i dont use. In this case its Evolution. 

Im running synaptic in advanced mode and marks evolution for complete removal, but after that is says that "ubuntu-desktop" needs to be removed to, why? i only want to remove evolution, not the desktop, or anything else. :???:

---

### Post by Adrian_b on 2006-02-27
It's okay, ubuntu-desktop is a metapackage, which means:
When you install ubuntu-desktop, you install evolution, gnome-terminal and so on.
However, when you remove ubuntu-desktop, you don't remove any of those packages. (Believe me, i just uninstalled evolution)

---

### Post by jimpa on 2006-02-27
aight, i deleted evolution,  but there is still some packages related to evolution that did not get removed, can i remove them to?

---

### Post by kaamos on 2006-02-27
I think everything but evolution-data-server is safe to remove.

---

