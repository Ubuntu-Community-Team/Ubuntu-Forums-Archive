---
title: "KDE kicks me out to the login screen after a few seconds"
date: 2009-11-22
forum: Desktop Environments
---

### Post by Pikestaff on 2009-11-22
Hello all,

Happy K/Ubuntu user since 6.06 here.  However I just began having an unusual problem a few moments ago; namely, I can no longer log into KDE because it automatically logs me back out and kicks me to the login screen a few seconds after it starts up.

I sort of suspect it might have to do with one of my programs, because I can see all my programs pop up one by one-- first Pidgin, then Deluge, and then Amarok... and then KDE usually dies right around the time that Amarok shows up.  I'm not sure how to go about closing these programs, though, because KDE dies before I can :p

This isn't a particularly crucial problem because in the meantime I seem to be using Gnome with no issues, but I do prefer KDE so any advice would be appreciated!

For what it's worth, Firefox was acting really bizarrely right before this whole KDE issue started happening: constantly crashing for no reason, losing all my saved tabs, etc.  I thought I'd finally fixed Firefox but then KDE decided to be a bad toy, so... yeah :neutral:  Not sure if that has anything to do with it.  Regardless, any advice would be loved! <3

P.S. Already did a fsck, it showed no errors.

**EDIT**: Fixed already, turns out it was some sort of weird FoxyTunes/Amarok thing.  Uninstalled FoxyTunes and I'm up and running again.  Hope it helps someone else!

---

### Post by HeadHunter00 on 2009-11-22
Install gdm. Then "sudo dpkg-reconfigure gdm" and select gdm.:D

---

