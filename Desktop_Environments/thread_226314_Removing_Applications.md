---
title: "Removing Applications"
date: 2006-07-31
forum: Desktop Environments
---

### Post by miller0521 on 2006-07-31
I want to remove some of the stuff I never use, such as bluetooth stuff, gnome games and the like. However everything wants to remove ubuntu-desktop, which then ubuntu-desktop says that its used to grab upgrades. Is there a way to keep ubuntu-desktop yet remove things I don't want?

---

### Post by frodon on 2006-07-31
If this things a part of the gnome desktop like the games, totem, rhytmbox, ... this will be really difficult.
If you try to remove via synaptic an apps which is a part of the gnome desktop then synaptic will also remove the gnome desktop.

---

### Post by kbrooks on 2006-07-31
> **frodon said:**
> If this things a part of the gnome desktop like the games, totem, rhytmbox, ... this will be really difficult.
If you try to remove via synaptic an apps which is a part of the gnome desktop then synaptic will also remove the gnome desktop.

That is not true. ubuntu-desktop is a metapackage, a package that relies on other packages in order to pull them in. It CAN be removed: dependencies are not removed. APT only removes individual packages. It does not cascade into dependencies and remove them. You do need the metapackage for upgrades, so put it back in before upgrading!

---

### Post by frodon on 2006-07-31
Make the test trying to remove totem and see by yourself what happen.

---

### Post by ricesteam on 2006-07-31
I am too wondering what I should do with ubuntu-desktop.

Some say its safe to remove; some say its useful for upgrades...

---

