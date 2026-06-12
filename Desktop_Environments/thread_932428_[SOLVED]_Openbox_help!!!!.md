---
title: "[SOLVED] Openbox help!!!!"
date: 2008-09-28
forum: Desktop Environments
---

### Post by jimi_hendrix on 2008-09-28
bad post please remove

---

### Post by urukrama on 2008-09-28
**EDIT: The original question was how to bring up the client list menu when you don't have a middle mouse button.**

Try clicking both the left and right button simultaneously.

You can also change the settings in your rc.xml file (in ~/.config/openbox/rc.xml), and configure Openbox so that it launches that menu when you left click on the desktop (or whatever else you want), or bind it to a keybinding.

For a keybinding, you could add something like the following to the <keyboard> section to launch the menu when you press Alt+F3:

```
<keybind key="A-F3">
      <action name="ShowMenu">
        <menu>client-list-combined-menu</menu>
      </action>
    </keybind>

```

For a mousebinding, add something like the following to the <context name="Root"> section of the <mouse> section to launch it with the left button:

```
<mousebind button="Left" action="Press">
        <action name="ShowMenu">
          <menu>client-list-combined-menu</menu>
        </action>
      </mousebind>

```

Or the following if you'd like to launch it when you press Alt and right click:

```
<mousebind button="A-Left" action="Press">
        <action name="ShowMenu">
          <menu>client-list-combined-menu</menu>
        </action>
      </mousebind>

```

Make sure you place these in the right part of the file, or your configuration will break Openbox. Reconfigure Openbox (in the root menu) and the changes should take effect. If you have an error in your file, Openbox will tell you where it is when you reconfigure it.

---

