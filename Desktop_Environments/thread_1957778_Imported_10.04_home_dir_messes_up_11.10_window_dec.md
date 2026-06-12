---
title: "Imported 10.04 home dir messes up 11.10 window decorations"
date: 2012-04-13
forum: Desktop Environments
---

### Post by ThomasArildsen on 2012-04-13
I have recently freshly installed Ubuntu 11.10 (64 bit) on my PC. After installation, I have now replaced my home dir by my backed-up home dir from Ubuntu 10.04. At first glance everything seems OK. The only exception is that it seems to have messed up the window frames of programs not running maximized. They seem to have reverted to some old-fashioned default.
It's not a major show-stopper, but it does not look good. I have attached an example screenshot of Banshee.
Any idea where to fix this? Somewhere in my home dir, I suppose ;-)

---

### Post by slooksterpsv on 2012-04-13
Personally, what I would do is this: open a terminal (via Dash-> type in terminal) and then type in rm -R ./.config
log out and log back in. This will purge any configurations you have setup for any applications. Alternatively you can cd into the .config directory and remove just the gnome items by doing the following:

cd .config
ls

find the gnome, gtk, etc. directories you want to remove and do this:

rm -R ./<gnome gtk or other folder>

---

### Post by kiirokurisu on 2012-04-13
Not quite... a lot of Gnome stuff is not stored under the .config directory. I'm afraid you've discovered one of the ugly truths of upgrading an Ubuntu install - often the upgrade goes fine but settings just don't translate correctly to the new versions of software. My solution is always to move aside my entire home directory by renaming it, before logging in for the first time to a new/upgraded install. This causes completely fresh config to be created. I then selectively bring across the folders containing data for various apps in my home directory. This is the only foolproof method in my experience.

---

### Post by ThomasArildsen on 2012-04-13
Well, I have backups of both the old and new home dir, so I guess I will just try replacing some '.something_that_sounds_relevant' directories in my home dir with those from the backed-up clean-slate 11.10 home dir and see what happens.
Thanks for you suggestions.

---

### Post by atarixle on 2012-04-13
In GNOME3 a.k.a. Unity, Themes only really work when installed in /usr/share/themes ...

The folder ~/.themes (and ~/.fonts) aren't really well supported yet.

---

### Post by ThomasArildsen on 2012-04-16
I solved the problem now. All it took was to fiddle around a little with the appearance settings in the system settings tool (changed the theme from Ambiance to Radiance and back). This seems to have overwritten the broken settings and the desktop now looks perfectly 11.10-like.

---

### Post by mcduck on 2012-04-16
> **atarixle said:**
> In GNOME3 a.k.a. Unity, Themes only really work when installed in /usr/share/themes ...

The folder ~/.themes (and ~/.fonts) aren't really well supported yet.

Care to expand this a bit? As far as I'm awae, the themes installed in user home directory work just as well as always before. And Gnome's release docs or bug reports don't mention anything about such limitations either...

Are yuou sure yuou haven't just tried using GTK2 themes or had problems with apps running as root (and thus requiring the theme to be installed in systemn directory instead of user home, or linked to root's home, just like in all previous Gnome versions)?

---

