---
title: "Debian base install vs. Ubuntu base install"
date: 2008-05-30
forum: Debian
---

### Post by timzak on 2008-05-30
I've read a lot about how much more responsive a Debian base install is compared to Ubuntu.  How do they match up if you do a base install of Ubuntu with their mini.iso?  Is Debian still more responsive?

Let's say we do an install of each, then add gdm, xfce4 and synaptic to the base install.  Are they pretty much on even footing now, or does Debian still have an advantage?

Thanks, I'm just trying to understand more.  :)

---

### Post by jdhore on 2008-05-30
> **timzak said:**
> I've read a lot about how much more responsive a Debian base install is compared to Ubuntu.  How do they match up if you do a base install of Ubuntu with their mini.iso?  Is Debian still more responsive?

Let's say we do an install of each, then add gdm, xfce4 and synaptic to the base install.  Are they pretty much on even footing now, or does Debian still have an advantage?

Thanks, I'm just trying to understand more.  :)

Basically, Debian will always be more responsive than Ubuntu even with doing a very base install. Here's why: Ubuntu enables almost every driver in the kernel and then, on top of that, adds the modules from linux-ubuntu-modules and linux-backports-modules, all of which have to be parsed to see if they have to be loaded which takes time (not much, but still). Also, Ubuntu installs a lot of stuff by default (again on the miniCD) that they think you'll need like dbus and apport and other stuff like that which also slows the system down. Sure, for newbies, it makes life a decent bit easier, but it is slower.

I personally think Ubuntu tries to be marginally better than Windows (XP) which they succeed at, but they're not any better than that which (in a few words) sucks.

---

