---
title: "Editing Gnome Source"
date: 2005-12-14
forum: Desktop Environments
---

### Post by domstyledesign on 2005-12-14
I'd like to peek around w/ the gnome source and maybe try my hand @ customization.  is there a devel package i can just install from apt-get, or should i download the source from their website?  what else do i need to know to get started?

---

### Post by ranf on 2005-12-14
[QUOTE=domstyledesign]I'd like to peek around w/ the gnome source and maybe try my hand @ customization.  is there a devel package i can just install from apt-get, or should i download the source from their website?  what else do i need to know to get started?[/QUOTE]
To get the source of package "X":
```

mkdir src
cd src
sudo apt-get source X
```
But Gnome consists of a whole lot of packages.

To get all build-dependencies for package "X":
```
sudo apt-get build-dep X
```

---

### Post by domstyledesign on 2005-12-14
so, specifically, i want to look @ the code for the window list panel applet.  do i really need to download all the stuff for gnome, or just the libwnck-dev package?

---

### Post by RAOF on 2005-12-14
You'd actually want to:
```
sudo apt-get build-dep libwnck
sudo apt-get source libwnck
```
The -dev packages are for building code which depends upon libwnck, not for building libwnck itself.

---

