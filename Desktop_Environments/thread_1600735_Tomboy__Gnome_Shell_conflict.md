---
title: "Tomboy / Gnome Shell conflict"
date: 2010-10-19
forum: Desktop Environments
---

### Post by steenledet on 2010-10-19
So, I've updated to Maverick and I'm running Gnome Shell at login, the version from the repos.

My problem is that Tomboy in the tray does does not list the titles of my notes. There's just the yellow note icon. The rest of the text (Synchronize, Preferences, etc) all work normally.

If I log in to the normal Ubuntu desktop, there is no problem with Tomboy.

Any ideas?

---

### Post by sharm on 2010-10-20
> **steenledet said:**
> So, I've updated to Maverick and I'm running Gnome Shell at login, the version from the repos.

My problem is that Tomboy in the tray does does not list the titles of my notes. There's just the yellow note icon. The rest of the text (Synchronize, Preferences, etc) all work normally.

If I log in to the normal Ubuntu desktop, there is no problem with Tomboy.

Any ideas?

Known bug in a patch applied by Ubuntu guys, fix committed and update on the way.  We (upstream Tomboy devs) are planning to add an unpatched deb in our PPA in the next day or two, which *may* get you a fix faster.

Bug: [https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/627744](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/627744)

PPA: [https://launchpad.net/~tomboy-packagers/+archive/stable](https://launchpad.net/~tomboy-packagers/+archive/stable) (don't use until you see a 1.4.x release in there)

---

### Post by steenledet on 2010-10-20
Awesome, thanks a bunch. I'll keep my eyes out for the PPA update :)

---

