---
title: "What not to copy in /home ?"
date: 2011-03-15
forum: Desktop Environments
---

### Post by dargaud on 2011-03-15
Hello all,
Linux has long made it easy to change system: just take /home/user and move it to the new system. Done. Or is it ? I noticed that if I do that, then the brand new shiny KDE seen on the first boot of the new system (before the copy), turn to an oldish looking style.

So the question is: are there some subdirectories of ~ that are better off not being copied ? Maybe .local, .kde, .cache, .dbus, .gnome2 ?

Thanks

---

### Post by kellemes on 2011-03-15
> **dargaud said:**
> Hello all,
Linux has long made it easy to change system: just take /home/user and move it to the new system. Done. Or is it ? I noticed that if I do that, then the brand new shiny KDE seen on the first boot of the new system (before the copy), turn to an oldish looking style.

So the question is: are there some subdirectories of ~ that are better off not being copied ? Maybe .local, .kde, .cache, .dbus, .gnome2 ?

Thanks

Guess it depends on what version of KDE to what version of KDE you're copying. Are they the same version?
I assume this is from Ubuntu to Ubuntu at least?

---

### Post by TBABill on 2011-03-15
You're right. Many suggest removing your /.* files/directories on the home partition so that your configuration items do not carry into the new install and bork the system, particulary if you move from one version to another. Obviously the system will be different so what you have setup in Kubuntu 10.04, for example, will be different than Kubuntu 10.10. Unless you want to try to retain those settings and see how they work, removing them will force the system to install the current config options instead, or at least that's my best understanding of it.

---

### Post by Krytarik on 2011-03-15
> **TBABill said:**
> Many suggest removing your /.* files/directories on the home partition
If I would do this, almost only the desktop background pictures would make it into the new home directory. :P
How about you, dargaud, would it still make sense then, to copy it *at all*?

---

### Post by dargaud on 2011-03-16
It doesn't matter which kde version it is, it's more like a generic question. And as for removing ~/.* there are plenty of things that are worth keeping... So, nobody has made a list of those non-critical ones ?

---

### Post by Krytarik on 2011-03-16
That depends of course on the apps you use. Actually it is the *critical* ones, those regarding the actual OS/DE, which may cause difficulties. So, the approach should be to retain as much as necessary/possible of your *real personal stuff*, and leave the rest behind. If you can't stay off of moving them all, you need to check "~/.xsession-errors" afterwards, and sort out the issues one-by-one, and be prepared that it may even happen that you don't get to a desktop at all after moving the files/dirs.

---

### Post by deconstrained on 2011-03-16
> **dargaud said:**
> Maybe .local, .kde, .cache, .dbus, .gnome2 ?

Thanks
All of the above, and then some.

The best way to make sure everything (settings, caches, etc) is copied seamlessly is with good ol' rsync.

But if your themes and fonts were installed system-wide on the old system they need to be installed system-wide on the new one, or the themes/fonts you're using simply won't work.

---

