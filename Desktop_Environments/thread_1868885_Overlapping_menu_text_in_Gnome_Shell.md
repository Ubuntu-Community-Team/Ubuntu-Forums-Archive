---
title: "Overlapping menu text in Gnome Shell"
date: 2011-10-24
forum: Desktop Environments
---

### Post by dpny on 2011-10-24
After changing to the [Nord theme](http://0rax0.deviantart.com/art/GNOME-Shell-Nord-214295138)  I am seeing distortion in the Gnome Menu bar. It looks like the menu for the desktop is being drawn under the Gnome Shell activity menu.

---

### Post by dpny on 2011-10-25
Oops

---

### Post by crdlb on 2011-10-25
That is indeed the nautilus menu bar. It is caused by the appmenu-gtk3 package. Remove it and restart nautilus. Alternatively, disable desktop icons in gnome-tweak-tool.

[link to bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771")

---

### Post by dpny on 2011-10-25
> **crdlb said:**
> That is indeed the nautilus menu bar. It is caused by the appmenu-gtk3 package. Remove it and restart nautilus. Alternatively, disable desktop icons in gnome-tweak-tool.

[link to bug]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/826771")

Thanks.

---

