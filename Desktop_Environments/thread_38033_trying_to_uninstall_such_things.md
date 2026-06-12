---
title: "trying to uninstall such things"
date: 2005-05-29
forum: Desktop Environments
---

### Post by simple on 2005-05-29
i don't use evolution mail, and don't plan on it and frankly dislike it being installed, so i try to uninstall it from synaptic and it wants to wipe away ubuntu-desktop? is ubuntu-desktop really dependent on evolutiongroupware suite or is there a way of removing things like this that i dont' want that want to also remove ubuntu-desktop

---

### Post by Leif on 2005-05-29
Yes, ubuntu desktop does depend on it, but this is really not a problem between releases. You probably should reinstall ubuntu desktop before upgrading to breezy, when it comes out tho.

---

### Post by simple on 2005-05-29
[QUOTE=Leif]Yes, ubuntu desktop does depend on it, but this is really not a problem between releases. You probably should reinstall ubuntu desktop before upgrading to breezy, when it comes out tho.[/QUOTE]
 why would it depend on an email retrieving client? and i don't plan on using breezy until it's realeased stable which i don't think is anytime soon is it?

---

### Post by cudaman73 on 2005-05-29
[QUOTE=simple]why would it depend on an email retrieving client? and i don't plan on using breezy until it's realeased stable which i don't think is anytime soon is it?[/QUOTE]

I believe that ubuntu-desktop is a dummy package for the basic ubuntu included programs. If that's true, then evolution is a default package (which makes sense, as it comes with ubuntu), and removing that would give you dependency problems with ubuntu-desktop. My suggestion? leave it on there, unless you're running out of space. It's not doing any harm just sitting there, is it?

---

### Post by simple on 2005-05-29
[QUOTE=cudaman73]I believe that ubuntu-desktop is a dummy package for the basic ubuntu included programs. If that's true, then evolution is a default package (which makes sense, as it comes with ubuntu), and removing that would give you dependency problems with ubuntu-desktop. My suggestion? leave it on there, unless you're running out of space. It's not doing any harm just sitting there, is it?[/QUOTE]
well it's stupid to be just sitting there, if it just sits there it might as well not be there at all, so help getting rid of it would be the next reply i hope

---

### Post by Leif on 2005-05-29
[QUOTE=simple]why would it depend on an email retrieving client? and i don't plan on using breezy until it's realeased stable which i don't think is anytime soon is it?[/QUOTE]

Ubuntu-desktop is just a meta-package that describes what the developers feel is the default ubuntu "experience". Removing it does not break anything, but it may be tied to changes made to breezy, that's why I suggested reinstalling it when the time comes. And that should be in October, so plenty of time.

---

### Post by tread on 2005-05-29
Yep, exactly - ubuntu-desktop is a meta package containing the packages installed by default. If it gets removed now, not a problem. You would want to install it before upgrading to breezy finally, so if they add something like beagle to ubuntu-desktop that would get installed too.

---

### Post by cudaman73 on 2005-05-29
[QUOTE=simple]well it's stupid to be just sitting there, if it just sits there it might as well not be there at all, so help getting rid of it would be the next reply i hope[/QUOTE]

I agree, but it's sort of like windows and IE. If it's integrated into the desktop, it shouldn't be removed. Synaptic's description of ubuntu-desktop is as follows.

[I]The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

[B]It is safe to remove this package if some of the desktop system
packages are not desired. [/B] However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).[/I]

---

