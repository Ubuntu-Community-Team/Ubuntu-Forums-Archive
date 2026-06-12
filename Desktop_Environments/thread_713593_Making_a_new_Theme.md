---
title: "Making a new Theme"
date: 2008-03-02
forum: Desktop Environments
---

### Post by Neon612 on 2008-03-02
How can I make a new theme for Ubuntu if I get into the gtkrc file from a installed theme, edit it and try to save a copy of it in the /usr/share/themes/ directory it won't let me save a copy.

I want to try my hand at making a theme but when I go to save the gtkrc file it won't let me. What do I do to save the file where I can get it to be a theme that can be used in The Widget Factory or even to actually be set in the system?

---

### Post by bharadwaj on 2008-03-03
in which environment are you trying to make your theme for GNOME, KDE or XFCE?
If you want tro replace the theme file acces it from > gksudo nautilus

---

### Post by Neon612 on 2008-03-03
I'm in whatever the default environment is in Ubuntu.

I;m not sure which one it is though.

---

### Post by spupy on 2008-03-03
Your themes aren't located at /usr/share/themes. You can find them in /home/yourusername/.themes/

---

### Post by xl_cheese on 2008-03-03
usr/share/themes are where the default installed themes are located.

You can easily copy them to /home/*/.themes for your local copy.

Synaptic and a few other apps will look odd when using a theme from the .themes dir.  When you arrive on a theme you like then you can put it in the usr/share/themes directory.

---

### Post by spupy on 2008-03-03
> **xl_cheese said:**
> usr/share/themes are where the default installed themes are located.

You can easily copy them to /home/*/.themes for your local copy.

Synaptic and a few other apps will look odd when using a theme from the .themes dir.  When you arrive on a theme you like then you can put it in the usr/share/themes directory.

They will look "odd" even if you use themes from /usr/share/themes. In this place are themes located for all users. This includes root, and synaptic and other administrative programs run under root. Even if you change your user's theme with the theme selector, you need to choose one for root separately with 
```
sudo gnome-theme-manager

```
(or whatever the theme selector was named under gnome)

---

