---
title: "Update Failed"
date: 2009-02-01
forum: General Help
---

### Post by Adrenochrom3 on 2009-02-01
okk i have an update for Cairo-Dock that fails to install everytime i try to install it.

in the details, it states:

Unpacking replacement cairo-dock ...
dpkg: error processing /var/cache/apt/archives/cairo-dock_1.6.3.1_all.deb (--unpack):
 trying to overoverwrite '/usr/share/cairo-dock/icon-mouse.png', which is also in package cairo-dock-data
dpkg-deb: subprocess paste killed by signal (broken pipe)
Errors were encountered while processing:
 /ver/cache/apt/archives/cairo-dock_1.6.3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

how do i finishing installing this package?

---

### Post by x33a on 2009-02-01
uninstall previously installed cairo-dock. remove all the configuration files (backup any tweaks you've made). then proceed with the latest install.

---

