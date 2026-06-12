---
title: "Completely prevent limited user from changing wallpaper"
date: 2009-05-12
forum: General Help
---

### Post by hashbrowns on 2009-05-12
I work at a training center, managing a small lab with computers running Jaunty. I would like these computers to be as locked down as possible while still running a normal copy of Ubuntu + Gnome. These accounts are all limited user accounts.

Some of the students, for laughs, like to change the desktop background into inappropriate pictures. I need a way to completely lock out this changing from happening. I already found the command to lock this out from the desktop context menu:

```
chmod 744 /usr/bin/gnome-background-properties
```

But that allows them to change the background by using Firefox, right clicking and doing 'set as desktop background' - so I installed the "menu editor' plugin into firefox and locked that down too, but I've discovered that they can still use 'Eye of Gnome' image viewer to do the same thing!

There must be some foolproof way to allow me to set the desktop wallpaper in these limited accounts, and then block anyone without administrative/sudo access from modifying it at all...but I can't figure out what it can be!

---

### Post by 3rdalbum on 2009-05-12
The program you want is called Pessulus, and it's available from the Ubuntu Repositories. It allows you to use Gnome's built-in lockdown features.

---

### Post by PengytheDuckwin on 2009-09-14
> **3rdalbum said:**
> The program you want is called Pessulus, and it's available from the Ubuntu Repositories. It allows you to use Gnome's built-in lockdown features.

That actually doesn't prevent changing wallpapers:(, but it does work nicely for the panel problem I've been having. Thanks!:)

BTW, I also have the same problem, But thankfully I might see a way to fix it. Is there a program or trick to prevent a gconf-editor value from changing?

---

### Post by Vaphell on 2009-09-14
you tried that?
[http://brainstorm.ubuntu.com/idea/1626/](http://brainstorm.ubuntu.com/idea/1626/)

quote:
Here is how to set the background, window and icon theme so no one but admin can change it.

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/background/picture_filename /usr/share/backgrounds/warty-final-ubuntu.png

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/interface/gtk_theme Human

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/interface/icon_theme Human

---

