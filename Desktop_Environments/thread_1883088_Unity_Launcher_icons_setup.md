---
title: "Unity Launcher icons setup?"
date: 2011-11-18
forum: Desktop Environments
---

### Post by pepribal on 2011-11-18
So far, the only way I've seen to add icons to the launcher is to have the application executed, and then tell it to keep the icon in the launcher.

But why I cannot find the way to tell: "add this icon to the launcher, with a command line like blender -W", for example. Why can't I edit the commands associated to the icons?

Please don't tell me it cannot be done!

Thx.

---

### Post by Frogs Hair on 2011-11-18
Take a look at this thread . [http://ubuntuforums.org/showthread.php?t=1746553&highlight=Blender+icon+unity](http://ubuntuforums.org/showthread.php?t=1746553&highlight=Blender+icon+unity)

---

### Post by pepribal on 2011-11-18
The Blender thing was just an example... What I want to know is if I can edit my launchers, edit the command lines, etc., or, if it can be confirmed that this new desktop is a huge step back.

Thx.

---

### Post by lynrock on 2011-11-19
Yes you can. If you open the *.desktop file in /usr/share/applications you can edit the EXEC line. In fact it is possible to add a menu to the launch icon and have multiple boot options.

---

### Post by stinkeye on 2011-11-19
If you want to edit a .desktop file in /usr/share/applications
it's better to copy the file to ~/.local/share/applications
and edit from there, and then drag to the launcher.

You can edit the file by dragging and dropping in gedit.

---

