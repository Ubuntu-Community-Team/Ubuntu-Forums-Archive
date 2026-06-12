---
title: "Totem"
date: 2006-09-07
forum: Desktop Environments
---

### Post by lwr on 2006-09-07
Totem says it wants to upgrade, which is fine by me, only I use the xine packages and when I click on upgrade it says totem-xine will be uninstalled and replaced with totem-gstreamer. How do I get around this?

---

### Post by whizbaby on 2006-09-07
Have *totem* and *totem-gstreamer* not been completely removed during the install of totem-xine? That should have happened (do it manually if not)! By the way, how did you install totem-xine?

---

### Post by lwr on 2006-09-07
I'm using synaptic because i'm lazy. If I mark totem for either removal or complete removal, it says I also need to remove ubuntu-desktop. I'm guessing I don't want to do that.

---

### Post by whizbaby on 2006-09-07
It depends. I think ubuntu-desktop is only a bundle of dependancies and safe to uninstall (this is what synaptic shows if you just select (click-with-mouse-on-name) the package):

The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system).

So it's only good for *getting* the software selected for ubuntu-desktop, after that you can remove it without hesitation(like it says) and remove the packages I suggested. (totem actually tries to upgrade just *because*) ubuntu-desktop is installed!)

---

