---
title: "Edit keyboard shortcuts with script or command line"
date: 2014-12-03
forum: Desktop Environments
---

### Post by vide_infra on 2014-12-03
I'm looking for a way to edit the keyboard shortcuts either through a script or through command line. I know you can manually edit them through System Settings>Keyboard>Shortcuts.

I need an automated way to set the Ctrl+Alt+Del shortcut to "Disabled". I've searched and have yet to find any way to edit with script/command line.

No, I'm not looking to use another program to manage this like gconf-editor. Also, commenting out the command in /etc/init/control-alt-delete.conf doesn't work as needed.
Running Ubuntu 12.04.5 LTS.

Thanks.

---

### Post by CantankRus on 2014-12-03
This tested on Trusty.

To disable....
```
gsettings set org.gnome.settings-daemon.plugins.media-keys logout ''
```

To reset to default (ctrl+alt+DEL)...
```
gsettings reset org.gnome.settings-daemon.plugins.media-keys logout
```

---

### Post by mc4man on 2014-12-03
Well I don't have any 12.04 installs around but if it (at a default) is in gconf than you should be able to change with a gconftool-2 -s command 
(you need to find the  type,  path & value.  Take a look in gconf-editor to discover those.

---

