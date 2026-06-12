---
title: "How to uninstall pulseaudio without uninstalling ubuntu-desktop."
date: 2009-05-09
forum: General Help
---

### Post by dragos240 on 2009-05-09
this has occured to me for the longest time. I can't stand it anymore! And if I try to remove it, i will remove ubuntu-desktop as well. I want to remove it once and for all. How!?

---

### Post by Sealbhach on 2009-05-09
As far as I know, that's OK, ubuntu-desktop is a meta package, like an empty wrapper, not needed anymore. I just checked, I don't have it installed anymore.

Wait for others to advise though. 

.

---

### Post by dragos240 on 2009-05-09
thanks

Im going to try it, last time someone uninstalled it, they complained about logging into a black screen, I think it was a console login they were talking about.

---

### Post by Mr. Picklesworth on 2009-05-09
Then go ahead and remove it. ubuntu-desktop is just a metapackage; it depends on everything else that Ubuntu installs by default, doing absolutely nothing itself other than depending on, recommending and suggesting packages. As long as nothing important goes with it, you will be fine.

Also, don't worry about this breaking upgrades. If you have a recent version, there is an ubuntu-minimal (and I believe ubuntu-standard) package that does the same kind of job as ubuntu-desktop, depending on less desktopy stuff.

---

### Post by Yellow Pasque on 2009-05-10
As said, ubuntu-desktop is just a metapackage that points to everything in a default installation of Ubuntu. Since pulseaudio is one of those packages, you can't remove it without removing the metapackage that points to it.

When I do a fresh install of Ubuntu, ubuntu-desktop quickly gets removed in the first wave of my optimizations (i.e. eliminating bloat i don't need).

---

### Post by gn2 on 2009-05-10
It's easier to build up from a minimal install CD than to strip down from a desktop install CD.

Have no fear of removing ubuntu-desktop, it only calls other packages for installation.
Mark it for removal in Synaptic and only one package will be removed.
Similarly, using Synaptic you can uninstall ubuntu-restricted extras and none of the extras will be removed.

---

