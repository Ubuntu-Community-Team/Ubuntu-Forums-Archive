---
title: "Updating via command line"
date: 2006-03-13
forum: Desktop Environments
---

### Post by kidcharles on 2006-03-13
I know how to run Update Manager in Gnome to do automatic updates for Ubuntu, but how can I do that via command line?

---

### Post by Gustav on 2006-03-13
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by bluevoodoo1 on 2006-03-13
[QUOTE=kidcharles]I know how to run Update Manager in Gnome to do automatic updates for Ubuntu, but how can I do that via command line?[/QUOTE]


```
gksudo update-manager
```

---

### Post by kidcharles on 2006-03-13
Thanks buddy.

---

### Post by towsonu2003 on 2006-03-13
[QUOTE=Gustav]sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]
I believe that should have been
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by bryanl on 2006-03-13
The upgrade versus dist-upgrade is a confusing issue I don't see explained very often. You can get a clue by looking at 'man apt-get' - here is how I see it.

**upgrade** will not remove any installed package and not upgrade any package where the upgrade would conflict with something.

**dist-upgrade** tries to be smarter and upgrade the most important packages at the expense of those of lesser importance if necessary.

So with plain 'upgrade' you can get stuck with old packages that have dependencies that would conflict with newer, more important stuff that can't be upgraded because the old stuff would then be broken. With 'dist-update' the older packages would be sacrificed for the newer more important packages.

At least, this is what it looks like to me.

---

### Post by towsonu2003 on 2006-03-13
basically, imo, upgrade is fine to update your existing ubuntu version (5.10). after tweaking sources.list, dist-upgrade is commonly used to update your system from an older ubuntu version to a newer ubuntu version (5.10 -> 6.04).

---

### Post by Gustav on 2006-03-13
**upgrade** just upgrades your existing packages as long as no new packages have to be installed or no packages have to be removed.

**dist-upgrade** upgrades all existing packages *and* if the upgraded packages depend on some new packages that isn't installed those packages are installed. If the newly upgraded packages conflicts with some older package the old package is removed.

In most cases they cause the same result but if you use the unstable branch (dapper) you might have to use dist-upgrade some times and it has happend in the stable branch aswell.

It doesn't harm to use dist-upgrade and whenever the different commands produce different results, dist-upgrade works best (at least according to my experience).

---

