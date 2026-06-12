---
title: "Recompile  of Gnome"
date: 2012-05-31
forum: Desktop Environments
---

### Post by neuman1812 on 2012-05-31
So Im running Ubuntu 12.04 With Gnome Classic Desktop.  This will be run  like ubuntu server...but with a Gnome desktop.   That in mind. What Im looking to do is remove some extra stuff from the Gnome Shell that I wont need

Printer
Bluetooth Support
ScreenSaver

Based on [https://bbs.archlinux.org/viewtopic.php?id=122611](https://bbs.archlinux.org/viewtopic.php?id=122611)

It looks like I will have to recompile my gnome-shell..   Could someone point me in the right direction to get this started?

---

### Post by 3Miro on 2012-05-31
Look at Gentoo distribution, it can do exactly what you want very easily for pretty much all packages (not just Gnome-shell). 

You can recompile Gnome-shell and you can add options to the configure script, however, I don't think the components that you want to remove a part of Gnome-shell. I think those are separate packages that you can just remove from your system. 

You can also look at Arch Linux, packages in Arch generally have fewer dependencies.

---

### Post by neuman1812 on 2012-06-03
The problem I run into is if I try and remove printing and Bluetooth us the synaptic manager.   Gnome-Dekstop gets automatically selected as a dependency to be removed.


I will look into the Gentoo Dist.

---

