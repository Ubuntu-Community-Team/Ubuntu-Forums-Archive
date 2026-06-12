---
title: "[SOLVED] Gnome themes in gnome apps in kde"
date: 2008-06-26
forum: Desktop Environments
---

### Post by Woody1987 on 2008-06-26
I'm trying to get my gnome apps in kubuntu to use my gnome themes. I dual boot Ubuntu and kubuntu and have /home on a separate partition, both have the same username and are therefore both using the exact same configuration files. My gnome apps in kubuntu use a QT theme which doesn't look at all right. When i go to the GTK styles and Fonts option in kcontrol, i can select the style to use, unfortunately the only two options available are Qt and Raleigh which i don't want to use. The annoying thing is that it appears that i have to use either one of those. In Ubuntu my Qt apps use the KDE themes present in the /home directory, why don't my GTK apps use the themes already available? Is this possible?

---

### Post by p_quarles on 2008-06-26
GTK apps *will* use your GTK theme. Make sure they're not set (in Kcontrol) to use your KDE theme, and then run a theme-changing application (e.g., Gnome-settings-manager or gtk-chtheme) and select the theme you want.

---

### Post by Xiong Chiamiov on 2008-06-27
And, is there a compelling reason to dual-boot the *buntus?  You can install both packages and switch between them at login (or even run both at the same time).

---

### Post by Woody1987 on 2008-06-27
i tried what you suggested p_quarles. I installed gnome-settings-daemon (couldnt find gnome-settings-manager), but whenever i tryto run it i get

```

** (gnome-settings-daemon:16640): WARNING **: Couldn't connect to session bus: Failed to execute dbus-launch to autolaunch D-Bus session

** (gnome-settings-daemon:16640): WARNING **: Could not get a connection to the bus

```

I then tried gtk-chtheme but regardless of the theme i change to none of my gtk apps will accept it. 

In the appearence properties under gtk Styles and Fonts i have only two options availble to me for GTK styles:

1. Use my KDE style in GTK applications (dont want)
2. Use another style: (dropdown box)
[INDENT]2.a. Qt (dont want)[/INDENT]
[INDENT]2.b. Raleigh (dont want)[/INDENT]      

The two options availble are useless to me. Isnt there a button somewhere that says "Allow GTK apps to use GTK themes" ??

---

### Post by Woody1987 on 2008-06-27
Fixed it! i remove gtk-qt-engine deleted all instances of ~/.gtkrc* and reinstalled gtk-qt-engine. I now have alot more themes to choose from.

---

