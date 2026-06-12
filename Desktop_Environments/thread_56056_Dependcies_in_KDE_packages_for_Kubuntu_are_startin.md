---
title: "Dependcies in KDE packages for Kubuntu are starting to annoy me !"
date: 2005-08-11
forum: Desktop Environments
---

### Post by oobuntoo on 2005-08-11
I like Kubuntu a lot. It is my main desktop right now. I do, however, have issue with the way some packages for it are made. There are KDE applications that I need and some that I definitely don't need. The problem is that the applications I don't need got installed along with the ones I want and if I removed the ones I don't want then the ones I want got removed as well due to package dependency. Take kdemultimedia package for example: I want to keep kmixer and remove Juk, but removing Juk will remove everything that are part of kdemultimedia package, including kmixer. There are other packages that are packaged in this manner. Try uninstalling kfloppy and see what else is getting uninstalled as well. My kmenu is cluttered with tons of stuffs that I've never used. Knowing that my system is filled with applications I don't want bugs me!
I don't know if this is KDE issue or just how package maintainer decided the way it should be. Is this common to all Debian-base distros or just Kubuntu? Does any one know of any other distros that don't package the KDE this way?

---

### Post by coolclassic on 2005-08-11
I might be wrong but my understanding is:

Any piece of software will always relay on another to run this would apply to windows as well. In windows the diffrence is that their is many duplications of the same file all held by different programs, thus the reason for such large software files.

In Linux (being Open sourced) we share files so one program being installed will use files from other packages unfortunatly this may mean some packages will get installed which has some resource which your piece if software needs.

---

### Post by gingermark on 2005-08-11
You're confusing pakages with metapackages. Metapackages provide an easy way of installing many programs at the same time. Take Kubuntu-desktop as an example. This will install a load of programs that make up the default desktop package.

If you uninstall one of the programs, you don't have the metapackage installed anymore, so it is removed from the list of your installed programs, but the remaining programs should remain. I think.

As a test, try uninstalling Juk - if it uninstalls all the other kdemultimedia packages then you can always reinstall them. But that shouldn't happen.

---

### Post by SGC on 2005-08-11
[QUOTE=gingermark]You're confusing pakages with metapackages. Metapackages provide an easy way of installing many programs at the same time. Take Kubuntu-desktop as an example. This will install a load of programs that make up the default desktop package.
If you uninstall one of the programs, you don't have the metapackage installed anymore, so it is removed from the list of your installed programs, but the remaining programs should remain. I think.

As a test, try uninstalling Juk - if it uninstalls all the other kdemultimedia packages then you can always reinstall them. But that shouldn't happen.[/QUOTE]


gingermark is right,  All base kde packages (kdepim, kdegames, kdemultimedia, kdenetwork,kdegraphics,etc...) are meta packages. Removing them will not removes the packages that comes with them.

So removing juk will not remove the packages that cames with kdemultimedia, it only only removes juk and the meta package kdemultimedia which is used only as an easy way of installating many packages, its even less than 1 kb.

---

### Post by oobuntoo on 2005-08-11
You're right, I was confused. When I tried to remove Juk, Synaptic said kdemultimedia will be removed as well. So I assumed that everything that were installed, when kdemultemedia was installed, would also be removed. I was afraid to remove kdemultimedia, but removing it didn't removed anything else besides Juk. However installing kdemultimedia will install tons of crap I don't need. Anyway, I misunderstood this whole metapackage concept. It was made clear by package manager like Synaptic.

---

