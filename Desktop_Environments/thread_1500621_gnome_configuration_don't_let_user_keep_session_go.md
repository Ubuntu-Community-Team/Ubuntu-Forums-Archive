---
title: "gnome configuration: don't let user keep session going"
date: 2010-06-03
forum: Desktop Environments
---

### Post by bcrowell on 2010-06-03
In recent versions of ubuntu, the behavior of gdm and gnome is changed so that if a gnome user doesn't touch the mouse or keyboard for a while, the session is locked, and they have to type their password in order to get back in. I dislike this behavior, because on some of the machines I use and manage, people will walk away and not come back, and then there is no way to log them out. I can switch and log in as a different user, but the AWOL user's session is sitting there eating up resources until the machine is rebooted. I prefer the old behavior, with no locking. Is there any way to get the old behavior back? I've looked through the gdm.conf docs, but can't seem to find anything relevant. This actually seems more like a gnome issue than a gdm issue. I think what's changed is that gnome now invokes a screensaver after a certain amount of time, and that screensaver locks the session.

---

### Post by TheStroj on 2010-06-03
Go to System - Settings - Screensaver and set it not to lock (it's 2 clicks dude, don't need any advanced terminal stuff :P)

---

### Post by bcrowell on 2010-06-03
> **TheStroj said:**
> Go to System - Settings - Screensaver and set it not to lock (it's 2 clicks dude, don't need any advanced terminal stuff :P)

Thanks for the reply. However, I want this to happen by default for other users, rather than having to set it by hand for every user who has an account on machines I manage. In order to set it for all those users using the Gnome GUI, I would actually have to know their passwords and log in as them. I don't know their passwords and don't want to log in as them.

---

### Post by bcrowell on 2010-06-03
I figured out something that works, although it's not really optimal. I can just do an apt-get remove gnome-screensaver.

---

### Post by TheStroj on 2010-06-03
> **bcrowell said:**
> I figured out something that works, although it's not really optimal. I can just do an apt-get remove gnome-screensaver.

or you can set it not to run on boot which would be almost the same thing

---

