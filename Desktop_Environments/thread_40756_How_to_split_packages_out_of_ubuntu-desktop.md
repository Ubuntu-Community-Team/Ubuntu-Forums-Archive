---
title: "How to split packages out of ubuntu-desktop"
date: 2005-06-10
forum: Desktop Environments
---

### Post by Nicolinux on 2005-06-10
Hi,

I had to uninstall ubuntu-desktop because I had to compile my own openssh-client with opensc support. Is there a way to install it without beeing forced to install the old openssh-client package again? Is it possible to tell apt to "mark" my custom openssh-client package as the dependancy to ubuntu-desktop?


Thanks,
Stefan

---

### Post by Joeb on 2005-06-10
[QUOTE=Nicolinux]Hi,

I had to uninstall ubuntu-desktop because I had to compile my own openssh-client with opensc support. Is there a way to install it without beeing forced to install the old openssh-client package again? Is it possible to tell apt to "mark" my custom openssh-client package as the dependancy to ubuntu-desktop?


Thanks,
Stefan[/QUOTE]


If I'm not mistaken, ubuntu-desktop is just a wrapper of packages and doesn't contain anything itself (but dependencies).  You should be able to continue on just fine without having to reinstall it.

---

### Post by Nicolinux on 2005-06-11
Yes, but then I loose the update notifications for the meta package ubuntu-desktop.


Stefan

---

### Post by Joeb on 2005-06-11
[QUOTE=Nicolinux]Yes, but then I loose the update notifications for the meta package ubuntu-desktop.


Stefan[/QUOTE]

While that is true, I thought that it only actually changes during the development cycle and once released, it's fixed.  So, if you are running the development version, you might want it because packages are potentially being added, but once the version freezes, so does ubuntu-desktop.

---

### Post by az on 2005-06-11
Just remember to reinstall ubuntu-desktop when you dist-upgrade to the next version.

---

