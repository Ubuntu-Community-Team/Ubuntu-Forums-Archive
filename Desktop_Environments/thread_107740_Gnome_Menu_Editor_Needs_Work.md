---
title: "Gnome Menu Editor Needs Work"
date: 2005-12-23
forum: Desktop Environments
---

### Post by pappo on 2005-12-23
Is there an equivalent menu editor the one used by KDE, but for Gnome ?
I have right-clicked on the Breezy menu's and tried using the built in menu editor, but all that does is let you "uncheck" a menu item.  It does not let you completely delete or rename menu items from the editor.

Anyone know of a better way to edit menu's from a GUI or from the command line ?

Regards,

Pappo

---

### Post by briancurtin on 2005-12-23
you certainly can rename items. right click on an item, go to properties, and change the name.

as far as deleting, that ability is greyed out for some reason and i didnt find a way to get it to work. kind of weird.

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=pappo]Is there an equivalent menu editor the one used by KDE, but for Gnome ?
I have right-clicked on the Breezy menu's and tried using the built in menu editor, but all that does is let you "uncheck" a menu item.  It does not let you completely delete or rename menu items from the editor.

Anyone know of a better way to edit menu's from a GUI or from the command line ?

Regards,

Pappo[/QUOTE]

I think the smeg package will give you a nice GUI menu editor for any freedesktop.org menu.

---

### Post by cstudent on 2005-12-23
[QUOTE=cwaldbieser]I think the smeg package will give you a nice GUI menu editor for any freedesktop.org menu.[/QUOTE]

I believe the built-in Gnome menu editor in Breezy is smeg. The developer of smeg has renamed his package Alacarte ([http://ubuntuforums.org/showthread.php?t=82537)](http://ubuntuforums.org/showthread.php?t=82537)).

As far as editing menu items in Gnome from the command line. The menu items are stored in /usr/share/applications and are named whatever.desktop. You can edit them in the text editor. You can also create menu items for other programs that may not usually have a place on the menu.

```

sudo gedit /usr/share/applications/whatever.desktop

```

You can browse the /usr/share/applications directory and open an existing menu item in the text editor to see how the file is laid out. Any new items you'd want to make you can just follow the format and you just change the properties.

This is a basic .desktop file layout:

```

[Desktop Entry]
Name=Azureus
Comment=Azureus
Exec=/opt/azureus/azureus
Icon=/opt/azureus/Azureus.png
Terminal=false
Type=Application
Categories=Application;Network;

```

---

