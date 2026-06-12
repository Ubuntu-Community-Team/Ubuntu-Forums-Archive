---
title: "Intrepid without KDE4?"
date: 2008-11-16
forum: Desktop Environments
---

### Post by pickarooney on 2008-11-16
Is it possible to upgrade from Hardy to Intrepid without KDE4 automatically replacing KDE3?
When I upgraded my laptop, I lost all my personalised settings - menus, wallpaper, kicker, screensaver... and found a pig-ugly Vista imitation in its stead. I just need to know if this is avoidable before I decide on updating my desktop.

---

### Post by awakatanka on 2008-11-16
Kubuntu intrepid doesn't have KDE3 anymore only KDE4. There is a thread about how to install KDE3 with intrepid, but with a update it will 1st replace it.

---

### Post by pickarooney on 2008-11-16
> **awakatanka said:**
> Kubuntu intrepid doesn't have KDE3 anymore only KDE4. There is a thread about how to install KDE3 with intrepid, but with a update it will 1st replace it.

Does it actually *un*install the KDE3 that was there in Hardy though? I know this is probably buried in the release notes somewhere, but it really would be nice if it were more obvious that an upgrade was going to destroy all your personal settings (and your graphics display, but that's another thread...)

---

### Post by jacksaff on 2008-11-16
All kde3 apps that have a kde4 equivalent get upgraded. if you have any kde3 apps without kde4 versions, they stay, plus whatever kde3 libs they require as dependencies. Once a program has a kde4 version the kde3 version is gone from kubuntu so if you don't want kde4, you can't upgrade.

It will be hard to get kde3 running in intrepid (just as it required a lot of work to let kde4 exist in hardy) as all of the names conflict. If you need a newer kernel and want to keep kde3 you're better off compiling a kernel for hardy than upgrading.

If you don't need a newer kernel, then hardy + backports should be fine for a year. Eventually people will stop backporting new software and you'll get stuck with old versions (and not just of kde stuff) but not for a while yet.

Your settings from kde3 will still be in your .kde file in your home directory and some can be reused. Desktop wallpaper and kicker settings will be useless though as the kde3 applications that formed the desktop have been replaced by plasma. You can, of course, tweak the look of plasma.

By the way, it WAS clear in the release notes that this would happen.

---

### Post by pickarooney on 2008-11-16
Thanks Jack. At least I had the foresight to test on an auxiliary machine if not to read the release notes :)

I'm going to start working on getting a decent Gnome-based setup going and once I'm happy with that I'll upgrade to Intrepid and say goodbye to KDE forever.

---

### Post by riseringseeker on 2008-11-24
> **jacksaff said:**
> All kde3 apps that have a kde4 equivalent get upgraded. if you have any kde3 apps without kde4 versions, they stay, plus whatever kde3 libs they require as dependencies. Once a program has a kde4 version the kde3 version is gone from kubuntu so if you don't want kde4, you can't upgrade.

No, 3.X apps do not stay with an upgrade, lost a couple of my favorite apps when upgraded to 8.10.  kworldclock and kdict to be specific.

---

