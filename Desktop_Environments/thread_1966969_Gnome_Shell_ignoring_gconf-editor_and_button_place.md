---
title: "Gnome Shell ignoring gconf-editor and button placement"
date: 2012-04-27
forum: Desktop Environments
---

### Post by alansmithee88 on 2012-04-27
I just upgraded from 10.04 to 12.04 and am slowly getting used to Gnome Shell. I have read plenty of documentation on changing the button layout in the windows via gconf-editor or gconftool, and have gone to /desktop/gnome/shell/windows/button_layout in an attempt to get close, minimize and maximize on the left. However, regardless of what I put there, the setting is disregarded and every window's controls are still on the right after restarting gnome-shell.

I have tried changing this key both with gconf-editor and gconftool via the command line:

```
$ gconftool --type string --set /desktop/gnome/shell/windows/button_layout "close,minimize,maximize:"
$ gconftool --get /desktop/gnome/shell/windows/button_layout
close,minimize,maximize:
```

Any tips?

---

### Post by alansmithee88 on 2012-04-28
FWIW, this also happens on a second machine, which was upgraded from 11.04 to 11.10 to 12.04.

---

### Post by wojox on 2012-04-28
Try dconf-tools
```
sudo apt-get update; sudo apt-get install dconf-tools
```
Open dconf-editor and set the values.

---

### Post by alansmithee88 on 2012-04-28
> **wojox said:**
> Try dconf-tools
```
sudo apt-get update; sudo apt-get install dconf-tools
```
Open dconf-editor and set the values.

That did it.

I found this link that also includes the exact key that needs to be changed: /org/gnome/shell/overrides

[http://dazedbyporndreams.com/how-to-place-the-windows-buttons-on-the-left](http://dazedbyporndreams.com/how-to-place-the-windows-buttons-on-the-left)

---

### Post by BCtom on 2012-04-28
Hi everyone,

I had the same problem; the gconf-editor would not work for me either. So, I tried another tweaking program called "Ubuntu Tweak," and it worked. I have no idea why gconf-editor does not work for me, but the buttons are now on the top right side of each window. I am, once again, a happy Ubuntu camper. :)

To find and load it:

[HTML]sudo add-apt-repository ppa:tualatrix/ppa[/HTML][HTML]sudo apt-get update && sudo apt-get install ubuntu-tweak[/HTML]Load it, then run it, either from Terminal, or find it in the Dash Home menu as "Ubuntu Tweak."

Goto Tweaks/Windows (under Desktop) and choose "Window control button position" at the top of the window. You chould see the change of the buttons instantaneously of all of your windows.

---

