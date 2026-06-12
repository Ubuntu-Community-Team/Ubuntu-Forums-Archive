---
title: "new needing help"
date: 2005-10-18
forum: Desktop Environments
---

### Post by mwolff on 2005-10-18
just started trying to learn linux, installed ubuntu this past weekend, liked the way the gnome allowed adding apps.  Now trying to setup kubuntu, running, but unable to find where to add apps.  I opened up the /etc/apt/sources.list file but still not sure where the software install is listed.

---

### Post by daller on 2005-10-18
Do you want a GUI app?

You can use Kynaptic! (K-menu -> System -> Package Manager)

Elseway you can do commandline:

sudo apt-cache search STRING

finding an application that you want, do this:

sudo apt-get install APPLICATION

Good luck! - And thank you for giving Kubuntu a try ;)

---

### Post by wjp.reg on 2005-10-18
Look in System | Admin | Synaptic

enter a search string for packages or browse the listing

sources.list is most likely set up for use.

Check this link [http://www.ubuntuguide.org/]("http://www.ubuntuguide.org/") for instructions for updating repositories in /etc/apt/sourcs.list

Oops, Daller, you beat me to it!

---

### Post by daller on 2005-10-18
As far as I can tell, he is looking for a KDE solution!

...But the commandline is the same everywhere :)

---

