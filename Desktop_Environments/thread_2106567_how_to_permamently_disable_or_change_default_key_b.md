---
title: "how to permamently disable or change default key bindings"
date: 2013-01-19
forum: Desktop Environments
---

### Post by detl_ on 2013-01-19
Hi,
I want to know how I can modify the default keybindings on my Ubuntu 12.10 system using Unity window manager.
I want to disable 'move window' keybinding ALT-F8 and ALT-F7.
I changed it in keyboad->shortcuts but every time I reboot my machine the default settings seem to be back.

Does somebody has got an idea what I can do ?

thank you,
detlef

---

### Post by stinkeye on 2013-01-19
Run each command in terminal...
```
gsettings set org.gnome.desktop.wm.keybindings begin-resize []
gsettings set org.gnome.desktop.wm.keybindings begin-move []
```

To revert changes use...
```
gsettings reset org.gnome.desktop.wm.keybindings begin-move
gsettings reset org.gnome.desktop.wm.keybindings begin-resize
```

---

### Post by detl_ on 2013-01-21
Hi, 
thank you. I added these lines to my .profile.
One thing is still open for me:

When I check the keys I can find 'panel-main-menu' is bound to ALT+F1.
This I also want to 'free' for my application. If I set it to [] however,
this has got no effect.
Seems there is another key binding config for unity ? 

Maybe you know that.
Thanks in advance.

detlef

---

### Post by stinkeye on 2013-01-22
The gsettings command
```
gsettings set org.gnome.desktop.wm.keybindings panel-main-menu []
```
should disable alt+F1 in dconf and
ccsm > Gnome Compatibilty
[ATTACH]230510[/ATTACH]

However there is another setting to disable in 
ccsm > Ubuntu Unity Plugin
[ATTACH]230511[/ATTACH]

---

