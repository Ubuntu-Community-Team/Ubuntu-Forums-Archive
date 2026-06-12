---
title: "ubuntu-desktop? (Solved)"
date: 2005-10-22
forum: Desktop Environments
---

### Post by abou on 2005-10-22
What exactly does the ubuntu-desktop package do? Synaptic says it is safe to uninstall. If I remove the OOo2 beta for the final version, ubuntu-desktop has to be removed; how necessary is it for the services it states in the Synaptic description and can it be re-installed without OOo2 beta?

---

### Post by matthew on 2005-10-22
ubuntu-desktop has nothing in it. It is a fake (called a meta-) file that lists as its dependencies all the programs that make up the standard desktop installation in Ubuntu. When you uninstall ubuntu-desktop no programs are removed, but all the desktop programs won't be automatically upgraded when/if you decide to use dist-upgrade to upgrade to the next Ubuntu release. You can remove it safely. If you decide to do the dist-upgrade in the future, just reinstall ubuntu-desktop to make the upgrade smoother.

---

### Post by abou on 2005-10-22
So no worries then. :p

---

### Post by matthew on 2005-10-22
[quote=abou]So no worries then. :p[/quote]
Precisely

---

### Post by Sirin on 2005-10-22
[QUOTE=abou]So no worries then. :p[/QUOTE]

But you're not gonna gain anything by removing it either. ;)

---

