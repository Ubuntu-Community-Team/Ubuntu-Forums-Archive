---
title: "KDE removal"
date: 2008-06-10
forum: Desktop Environments
---

### Post by joechummer on 2008-06-10
I installed KDE4 to see how it would do on my machine, and then decided to remove it.  However, uninstalling it from Synaptic merely got rid of the desktop environment and left literally dozens of KDE apps floating around in my Applications menu that I don't really have a use for anymore.  Is there any way to get rid of them all without going into Synaptic and uninstalling them all one at a time?  After all, I installed KDE from a single package, which apparently installed all of these other apps;  by this logic, when I uninstalled KDE, why didn't all of these apps uninstall too?

---

### Post by BLTicklemonster on 2008-06-10
I fall for it at least every 6 months, and regret it every time. KDE is just too different for my taste. I have no idea how to get rid of all the extra stuff other than go to synaptic and start looking in the letter K and work your way down the klist.

---

### Post by joechummer on 2008-06-10
KDE isn't THAT bad.  Well, at least KDE3 isn't.

I have KDE3 on my Xandros-running EeePC, and that works just fine, but KDE4 just seems really buggy by comparison.  Right after KDE4 was released, I installed it on a really low end computer (which was my first mistake), and within 5 minutes of using it for the very first time, I'd somehow killed the entire desktop environment and had to reboot because I couldn't get it back.  Upon rebooting, the lower panel was completely gone and I had to delete some config files just to get it back.  Not to mention all of the graphical glitches, which still occurred even on this higher PC.

---

### Post by Zorael on 2008-06-10
I'd say KDE 4 isn't really ready for general use yet. The 4.0.4 version in the repositories is awful. The 4.1b1 one that you can get from the extra ppa repo listed over at kubuntu.org's news post is much better. Regardless of how the version nomenclature may fool you, it should (in my opinion) still be considered as heavily under development. If you want to judge KDE, judge it by KDE 3.

kubuntu-kde4-desktop is a virtual package, which contains links and references to other packages. Think of it as a bundle. Removing this bundle doesn't remove all it contained unless you use certain terminal commands (anything aptitude does, or apt-get autoremove), likely because developers didn't want it to cause a chain reaction which would remove all kinds of apps you didn't want removed. (Imagine the clamor.)

To remove *all* apps that contain 'kde4' in its name, enter this in a terminal. This usually does the trick; it's what I've done to remove it, several times now.
```
$ sudo aptitude purge ~nkde4
```

---

