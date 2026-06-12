---
title: "Need some help with dconf CLI nomenclature"
date: 2014-04-18
forum: Desktop Environments
---

### Post by kansasnoob on 2014-04-18
I'm trying to work on a Trusty update to my Precise Classic thread:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Using dconf Editor I found what I was looking for in "org.gnome.desktop.wm.keybindings panel-run-dialog":

[ATTACH=CONFIG]252189[/ATTACH]

Oddly it was set to disabled even though the default is Alt+F2.

Anyway I was able to fix it just by clicking on Set to Default, but I'd like to be able to change that setting via CLI, eg;

NOTE: these do NOT work - therefore no code tags :)

gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog ['<Alt>F2']

gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog ['disabled']

I've also been playing with variants like:

dconf reset -f /org/gnome/desktop/wm/keybindings panel-run-dialog

But to no avail :cry:

I'm having a very tough time figuring out some stuff - like restoring all defaults - since the flashback sessions started using 'unity-settings-daemon' and 'unity-control-center' instead of the GNOME versions of those same packages.

Any thoughts?

---

### Post by mc4man on 2014-04-18
You need to quote the 'as', ie.
```
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog "['<Alt>F2']"
```

---

### Post by kansasnoob on 2014-04-19
> **mc4man said:**
> You need to quote the 'as', ie.
```
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog "['<Alt>F2']"
```

Thank you.

---

### Post by kansasnoob on 2014-04-19
This seems to be working OK:

```
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog "['<Alt>F2']"
```

Still studying variants:

gsettings reset org.gnome.desktop.wm.keybindings panel-run-dialog

dconf reset -f /org/gnome/desktop/wm/keybindings panel-run-dialog

The man pages for gsettings are at the very least confusing :(

But I have this working now:

[ATTACH=CONFIG]252215[/ATTACH]

---

