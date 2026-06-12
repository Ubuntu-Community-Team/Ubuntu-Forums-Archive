---
title: "The size of 1 of my 5 desktop icons can't be changed. (16.04)"
date: 2016-08-16
forum: Desktop Environments
---

### Post by lukon on 2016-08-16
After going from 14.04 to 16.04, one of my five nautilus desktop launchers had it's icon replaced with a generic looking plain white rectangle. This stupid icon is somehow special, in that it cannot be resized like the other 4 can. So when I shrink my icons using the "edit nautilus' global icon size" procedure, this one white one remains huge and sticks out like a big distraction.

Anyone got a solution?

---

### Post by ajgreeny on 2016-08-16
Can you change the icon itself by right clicking and choosing "Edit Launcher" or something similar then clicking on the icon shown in the dialogue box..

You may then be able to change the size if you wish, though that may depend on the DE you use; unity? xfce? gnome-shell?

Unity does not usually use desktop icons, though it is possible to add them if you really want or need to for some reason.

---

### Post by lukon on 2016-08-16
Thanks ajgreeny.

Ya. I've got Unity.

The icon seems immune from any revision in the GUI "dialog box" editor for the launcher. Right clicking the icon in the dialog box does nothing. Left clicking it brings up a home directory window, which makes absolutely no sense.

---

### Post by CatKiller on 2016-08-16
The reason it brings up the file chooser dialogue is because left-clicking on the icon lets you choose a new icon for it.

---

### Post by mc4man on 2016-08-16
Open a text editor then drag & drop the icon on to the editor. Post contents.

---

### Post by lukon on 2016-08-17
> **mc4man said:**
> Open a text editor then drag & drop the icon on to the editor. Post contents.

Thanks mc4man. Here it be:

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=nautilus
Name[en_US]=Luke Documents
Exec=nautilus /media/SLURP/Luke
Name=Tada
Icon=nautilus

Oh. CatKiller, now that does make sense. I seem to remember some old GUI editor that, when the icon was mouse-clicked, would show a library of other available icons, rather than a generic file navigation window. I guess since I was expecting the old library thing, the generic file window made no sense to me.

---

### Post by CantankRus on 2016-08-20
The default iconset in 16.04 doesn't have an icon named "**nautilus**".
In your .desktop file you posted for mc4man, change the icon to "**system-file-manager**".

You could also remove the lines containing  "[en_US]".

eg
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=nautilus /media/SLURP/Luke
Name=Tada
Icon=**system-file-manager**
```

PS: A custom .desktop file needs to be made executable.
You can also use the full path to an icon of your choice in the **Icon=** line.

---

### Post by lukon on 2016-08-22
Thanks, CantankRus. That fixes it.

---

