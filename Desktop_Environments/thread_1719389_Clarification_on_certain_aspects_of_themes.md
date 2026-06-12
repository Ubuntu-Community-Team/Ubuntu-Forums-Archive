---
title: "Clarification on certain aspects of themes"
date: 2011-04-01
forum: Desktop Environments
---

### Post by l07 on 2011-04-01
I have a theme and it has 3 folders: openbox-3, gtk-2.0, and gdm. gdm is for login? If so, it gets installed right when I drag it to appearance preferences?
Why doesn't the theme let colors be set in appearance preferences? Is there a way to edit themes with a gui? Because appearance preferences doesn't provide all possible customisations, like color of tooltips.

Also, I'd like to replace colors in icons by using gimp and opening each icon. Is there a way to batch replace?

---

### Post by Copper Bezel on 2011-04-01
The openbox and gdm themes will be for openbox and gdm respectively and won't be installed by dropping them into the Appearance Preferences window. GDM themes can't really be applied in Ubuntu, but they apply to other distros, and you can use openbox in place of Gnome/Metacity/GTK, but it's its own completely separate window manager.

If you're using Gnome, which I'm assuming, you can set tooltip colors, but some themes have certain colors locked down. It all depends on what GTK theme you're using. You can edit this in the theme file itself, but you'll need hexadecimal values for the colors you want to use. 

GIMP can do some batch editing, but I've never really played with that feature, so I can't really help with that.

---

### Post by 3Miro on 2011-04-01
For OpenBox themes, install Obconf (look for it in the software center). Form there you can select "install a theme" and add the theme that you want. You can also edit many other changes to OpenBox.

If you want to try different window managers, you can install Fusion-icon, which will let you select one click between Compiz, Metacity, OpenBox and others.

Ubuntu doesn't support GDM themes. You can install Ubuntu Tweaks to change the wallpaper and that's about all you can do.

---

### Post by l07 on 2011-04-02
What's the difference between Metacity and Compiz? They seemed to me like synonyms.

By doesn't support gdm you mean the support was dropped?

I understand window managers (openbox, gnome) but other distinctions aren't as clear (gdm, gtk, Metacity, Compiz). Does gtk and gnome mean the same thing?

---

