---
title: "How do I set the Default Desktop for new users"
date: 2008-07-13
forum: Desktop Environments
---

### Post by GrantsV on 2008-07-13
Hello,
As administrator of a network I want all newly created users to have a set desktop theme as standard.  When a new users is created where do the default profile settings come from in Ubuntu/Gnome linux?

Thanks for your help!

---

### Post by hehe22 on 2008-07-13
ok! thanks for this share!

---

### Post by daedae on 2008-07-13
gconftool-2 should do the trick, although there may be a better way to do this.  Much of the look and feel of the Gnome desktop can be altered via gconftool-2.  For example, to change the default desktop wallpaper you can use the following:

```
sudo gconftool-2 --config-source="xml::/etc/gconf/gconf.xml.defaults" --type string --set /desktop/gnome/background/picture_filename /usr/share/backgrounds/simple-ubuntu.png
```

Or change the default GTK theme:

```
sudo gconftool-2 --config-source="xml::/etc/gconf/gconf.xml.defaults" --type string --set /desktop/gnome/interface/gtk_theme Crux
```

Or the default Metacity theme:

```
sudo gconftool-2 --config-source="xml::/etc/gconf/gconf.xml.defaults" --type string --set /apps/metacity/general/theme Metabox
```

Mix and match anything you want.  It's fun to experiment.

---

### Post by coffeecat on 2008-07-14
There seems to be a solution posted in this thread:

[http://ubuntuforums.org/showthread.php?t=859002](http://ubuntuforums.org/showthread.php?t=859002)

---

