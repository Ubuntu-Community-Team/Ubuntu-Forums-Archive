---
title: "Reinstall Ubuntu Without Reinstalling"
date: 2006-01-08
forum: Desktop Environments
---

### Post by Drunken Pirate on 2006-01-08
I have kinda screwed up my Ubuntu installation, and I would like to reset my installalation. Is there any way I can uninstall every package I installed, and reset gnome?

---

### Post by aysiu on 2006-01-08
It's not worth it. It's safer and easier to reinstall, as Gnome itself is one of the packages.

When you reinstall, create a separate /home partition--that way, if you decide to reinstall again later, you can do so less painfully (keeping all your settings intact).

---

### Post by GTvulse on 2006-01-08
[QUOTE=Drunken Pirate]I have kinda screwed up my Ubuntu installation, and I would like to reset my installalation. Is there any way I can uninstall every package I installed, and reset gnome?[/QUOTE]
Insert your installation cd, making sure you have network connection (to reinstall updated files that may not be in the cache directory). Open Synaptic, make sure your installation cd is in the repository list or install it otherwise (with Edit->Install CD-ROM...). Reload repositories. Click on the column list tagged with an S. Select all the packages with a green box and mark for reinstallation (PAckages->Mark...). Hit apply and go have a stroll at the park.

---

### Post by leech on 2006-01-08
It sounds like me like it's just a configuration problem.  Just remove the .gnome, .gnome2, .gnome2_private, .gconf and .gconfd directory, that will reset your gnome to the default.  If that doesn't work, THEN do the stuff mentioned before..

Leech

---

### Post by Drunken Pirate on 2006-01-08
Thanks guys, seems like its easier to reinstall.

---

