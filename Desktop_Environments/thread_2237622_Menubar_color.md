---
title: "Menubar color"
date: 2014-08-03
forum: Desktop Environments
---

### Post by T-W-X on 2014-08-03
I installed Ubuntu-Desktop, hated Unity, and switched to Xubuntu/Xfce4.  The color of the Menubar (File, Edit, View, etc) is unacceptable and I can't find where to change it.

Where is this stupid setting at?

---

### Post by mooreted on 2014-08-03
In the lower right-hand corner of the Whisker menu there is an icon for settings. In settings there is a place to change themes. You can also right-click on the panel, click Panel and Properties. There are some settings in there as well.

---

### Post by T-W-X on 2014-08-03
Okay, WTH is a Whisker menu?

I've been through the Window Manager themes in the Settings Manager, and Ive been into the GTK Themes settings.

It appears that it might be inheriting the color from the display manager at login, but seems to have done so with two different display managers.

---

### Post by T-W-X on 2014-08-03
Nevermind, I just moved my home directory and created a new one since this is a new install.

---

### Post by tj-quinn on 2014-08-03
I had a similar problem when upgrading to 14.04. Didn't realise that whisker menu had been made the default. Replaced it with the old applications menu (panel preferences > add item) which respects the system theme (system settings > appearance and window manager.

---

### Post by T-W-X on 2014-08-03
After I nuked and recreated the home directory I did encounter it again as I changed XFCE themes, but it didn't persist and actually allowed the menubar color to change as I changed themes.  I suspect that somehow something got messed up in the stripping out of Unity along with manually installing Xfce4 before then installing the Xubuntu package to fill-in the gaps.

Getting this box running has been a huge PITA.  Been a Debian user for a long time, figured since at work I'm working with some Ubuntu servers I'd give Ubuntu a try.  Ended up loading Ubuntu Server first but somehow got mired in dependency hell when attemping to put a desktop environment on, something ended up wanting all of the i386 packages in addition to the amd64 stuff, then it started behaving really badly once it was finally up.  Pulled the drive out and put a fresh one in and put Debian Jessie on, but they've apparently decided they don't want to play ball with the older Geforce FX cards, so after fighting with that for several hours decided to nuke that and try a load of a desktop version of Ubuntu.  So far the only headache has been the window manager, we'll see.  Can't say that I'm a fan of using a GUI to admin the box; it feels unnatural, and with separate applets to configure GTK vs Xfce this isn't exactly endearing to me.

---

