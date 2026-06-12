---
title: "simple question about using repos to install ta3d"
date: 2008-12-04
forum: Gaming &amp; Leisure
---

### Post by Maric604 on 2008-12-04
I do not know why this is not working, it seems so simple.  These are the repositories listed on the ta3d download page:

deb [http://ta3d.darkstars.co.uk/apt/](http://ta3d.darkstars.co.uk/apt/) stable main
deb [http://ta3d.darkstars.co.uk/apt/](http://ta3d.darkstars.co.uk/apt/) testing main

but when I add them to the 'third-party software' list in 'software sources' and reload the package info nothing happens.  I have tried going to update manager and checking for new packages and going to add/remove programs and looking for 'ta3d' or something like it, but nothing shows up.  It just seems to do nothing.  What am I missing?

---

### Post by Vadi on 2008-12-04
I believe the packages the repository has are "tademo", "fmodex", and "allegrogl".

Also, you can see which repository provides which packages by clicking on "Origin" in Synaptic (bottom-left).

---

### Post by zuzuf on 2009-01-02
unfortunately some package managers may not show ta3d packages in "applications", but you can still install them from the full package list or from the command line:
to show the packages:
# apt-cache search ta3d

you should install ta3d (allegrogl and fmodex will be installed as dependencies) and tademo if you don't own a copy of Total Annihilation, the later will install resource files from the demo.

---

### Post by Vadi on 2009-01-03
zuzuf: if you'd like it to show in applications, here is a guide on how to do this: [https://wiki.ubuntu.com/GnomeAppInstallDesktopDatabaseAdd](https://wiki.ubuntu.com/GnomeAppInstallDesktopDatabaseAdd)

---

