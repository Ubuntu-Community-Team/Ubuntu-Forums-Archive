---
title: "Openbox root-menu"
date: 2008-02-05
forum: Desktop Environments
---

### Post by bsunde on 2008-02-05
I'd like to open up the openbox root menu with a key binding and have the menu appear in the upper left portion of my screen rather than directly under my mouse cursor.  Is this possible?

---

### Post by urukrama on 2008-02-05
As far as I know, you can't force the root menu to appear in a particular place, but you can bind it easily to a key combination. Open your rc.xml file (in /home/USERNAME/.config/openbox) in a text editor, and in the <keyboard> section of the file add the following:

> <keybind key="A-F1">
      <action name="ShowMenu">
        <menu>root-menu</menu>
      </action>
    </keybind>

This binds the menu to Alt F1. Change the keybind key to whatever you prefer. Reconfigure Openbox and the changes should have taken effect.

---

