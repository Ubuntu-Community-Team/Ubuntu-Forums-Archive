---
title: "Add the Programming Menu"
date: 2005-05-03
forum: Desktop Environments
---

### Post by outdooricon on 2005-05-03
I want to enable this menu, but can't figure out how. I ahve the menu-editor, but I can't add the Programming Menu with that. I have installed Jbuilder and just want to place it under "Programming" which doesn't yet show up.

---

### Post by kommissar on 2005-05-03
[QUOTE=outdooricon]I want to enable this menu, but can't figure out how. I ahve the menu-editor, but I can't add the Programming Menu with that. I have installed Jbuilder and just want to place it under "Programming" which doesn't yet show up.[/QUOTE]
This forum is NOT a place to ask questions, so your thread will likely be moved soon.  Read the forum FAQ and info.

If you want to add it to the GNOME Applications menu, and have done so with JBuilder, try opening a shell and typing 'killall gnome-panel' to refresh your menus.

---

### Post by outdooricon on 2005-05-03
Sorry about that, Admins please move this thread where appropraite. 

No, when I installed JBuilder it didn't put it in the Programming menu as there isn't one yet. I want to make that menu show up.

---

### Post by Ride Jib on 2005-05-03
Create a new file in your /usr/share/applications directory called jbuilder.desktop.
```

sudo gedit /usr/shar/applications/jbuilder.desktop

```
Inside this file place the following text:
```
[Desktop Entry]
Name=JBuilder
Comment=JBuilder Development Tool
Exec=<path to JBuilder executable>
Terminal=false
Type=Application
Categories=Application;Development;
Icon=<path to Icon image file.png>
```

---

