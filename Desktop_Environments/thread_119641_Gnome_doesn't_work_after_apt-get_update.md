---
title: "Gnome doesn't work after apt-get update"
date: 2006-01-19
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2006-01-19
For 5 days I've been trying to install Ubuntu (Breeze Badger) in a friend's computer but I always get the same problem: after a fresh install, I run apt-get update and afterwards Gnome freezes. I can interact with the login screen (gdm), but soon after I input my login name and password the screen freezes (although the mouse cursor keeps itself alive). I don't have any weird repository in my source.list, just the official ones. I don't even use Backports!!!

I've already installed Ubuntu in her computer 4 times (always doing a fresh install) but Gnome refuses to run after the update. That's really embarassing! My friend is almost reaching the conclusion that Windows XP (her previous OS) is the best thing she already had.

I don't believe it is a X problem because I can flawlessly login into KDE. 

Does anybody have any suggestion? 

About my friend's computer: Athlon XP 2100, 512 MB of RAM.

---

### Post by darth_vector on 2006-01-19
it freezes when you run update or upgrade?

it is safer to use aptitude and dist-upgrade, since these take greater care in handling dependencies and so forth.```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Marcos.Rufino on 2006-01-20
It freezes after an "apt-get update". This is very strange because the update is done soon after the install of the whole system. It shouldn't have any dependency problem at this point.

I've installed kubuntu after that (with the package kubuntu-desktop), uninstall all the gnome packages, and so tried all over again (doing apt-get install ubuntu-desktop).

---

