---
title: "Make GTK look nice in KDE?"
date: 2008-07-11
forum: Desktop Environments
---

### Post by bobbocanfly on 2008-07-11
I just switched to KDE 4.1 (Using the packages in the kubuntu-kde4-members PPA) but want to keep using some of my Gnome apps (specifically Firefox, Pidgin, Xchat and Banshee). At the moment they are really ugly (unthemed) and its really annoying. Is there a way to make GTK look nice in KDE?

---

### Post by spupy on 2008-07-11
In your home folder put a file named ".gtkrc-2.0". Here is what mine looks like:

```
gtk-theme-name="Murrina Deviant2"
gtk-icon-theme-name="Tango"
gtk-font-name="Sans 10"
gtk-toolbar-style=0
```

I think the options are self explanatory. The last one sets toolbars to display only icons without text beneath them.

---

