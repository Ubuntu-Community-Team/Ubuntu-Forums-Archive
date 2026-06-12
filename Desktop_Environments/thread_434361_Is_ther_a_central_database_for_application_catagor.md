---
title: "Is ther a central database for application catagorization?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by B-Con on 2007-05-05
Why is it that when I install, say, the KDE desktop environment, all the KDE apps show up in the Gnome Applications menu when I switch back to Gnome? How does Gnome know where to stick the KDE apps? Is there a central database managed by the OS where applications are organized and categorized, or does each display manager have to take care of that on its own? 

I would think that it would have to be central, otherwise each display manager would have to be editing *other* display manager databases in order to get their own apps to appear in the other DM's menus. If so, where is it and/or how can I access it. (Just curious.)

(Whoops, typo in the thread title. Bah.)

---

### Post by tgalati4 on 2007-05-06
Applications are cataloged using the Debian package management system, accessed through apt-get or synaptic.

KDE and gnome applications can run under either environment--provided you have the appropriate libraries installed.  You can have both gnome and KDE libraries installed and you can run both gnome and KDE apps in the same window manager.

Icons and menus are stored in your /home/user/.gnome or .kde directory so the apps show up in either window manager.  It can be confusing but most people mix and match KDE and gnome apps because they want the best tool for the job.

For me, K3b rocks as a CD burner, and I use it in Gnome.  The themes are not consistent between KDE and Gnome apps, but that's the way it is.  You can run a pure KDE environment, but then you will have to forcibly remove gnome applications that you don't want.  Since Ubuntu is based on gnome, it contains mostly gnome apps.  When you add KDE, you get a lot of KDE applications on top of all the gnome apps already installed.

If you want a clean KDE environment, try Freespire.

---

### Post by afoglia on 2007-05-06
I believe Ubuntu uses the FreeDesktop standard to share menus across all the different desktop environments.  That's how all the applications can be the same, because they are reading from the same source.  I'm not familiar with it, but the FreeDesktop specification explicitly says you can configure systems to use different menus in KDE and GNOME.  Check out [http://standards.freedesktop.org/menu-spec/latest/ar01s02.html]("http://standards.freedesktop.org/menu-spec/latest/ar01s02.html").  You'll probably have to keep digging, but it's a start.

---

