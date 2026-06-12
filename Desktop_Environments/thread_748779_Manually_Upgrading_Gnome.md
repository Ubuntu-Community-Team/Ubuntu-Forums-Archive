---
title: "Manually Upgrading Gnome"
date: 2008-04-07
forum: Desktop Environments
---

### Post by dicecca112 on 2008-04-07
How would one go about doing this, could it be done with just connecting to the Hardy Repos?  I don't want to upgrade fully to Hardy at this time

---

### Post by sdennie on 2008-04-07
Is there a specific reason you want to do this?  Because of the dependencies, it's not trivial to do and just upgrading gnome will probably cause most of your system to update.  If you are just looking for updated versions of 1 or 2 apps, you might be able to get away downloading the source code for the apps in question, building them and then using checkinstall to create custom .deb packages (I actually do this with the epiphany browser and it works fine).

---

### Post by benerivo on 2008-04-07
It could be done, although it is risky. Ubuntu isn't a full gnome distro, it picks and chooses some gnome packages that it considers useful (and also adds a few more that are not part of the standard gnome suite). What i think you would be upgrading is a package called ubuntu-desktop which is a 'meta-package' (ie. it is a collection of packages). You could do ```
gksudo gedit /etc/apt/sources.list
``` and then copy every line you have, then paste it on on to the end, and change gutsy to read hardy, so you would then have the repositories for both gutsy and hardy. Then go in to synaptic and 'reload', and then search for 'ubuntu-desktop' and upgrade that package.

---

