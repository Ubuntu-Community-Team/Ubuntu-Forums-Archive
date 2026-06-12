---
title: "Tweak tool"
date: 2016-05-30
forum: Desktop Environments
---

### Post by rosswmcgee on 2016-05-30
Running ubuntu 16.04 lts, Unity is fine, installed mate via synaptic, that went fine as well, installed mate tweak tool. When I click on tweak tool in mate  control center nothing happens?

How to fix?

---

### Post by QDR06VV9 on 2016-05-30
What errors are reported from the terminal.
```
mate-tweak
```

---

### Post by rosswmcgee on 2016-05-30
$ mate-tweak
Gtk-Message: Failed to load module "topmenu-gtk-module"
Window Manager is: marco
Traceback (most recent call last):
  File "/usr/bin/mate-tweak", line 1124, in <module>
    MateTweak()
  File "/usr/bin/mate-tweak", line 970, in __init__
    img = theme.load_icon(sidePage.icon, 48, 0)
GLib.Error: gtk-icon-theme-error-quark: Icon 'user-desktop' not present in theme Ambiant-MATE (0)

---

### Post by QDR06VV9 on 2016-05-31
> **rosswmcgee said:**
> $ mate-tweak
Gtk-Message: Failed to load module "topmenu-gtk-module"
Window Manager is: marco
Traceback (most recent call last):
  File "/usr/bin/mate-tweak", line 1124, in <module>
    MateTweak()
  File "/usr/bin/mate-tweak", line 970, in __init__
    img = theme.load_icon(sidePage.icon, 48, 0)
GLib.Error: gtk-icon-theme-error-quark: Icon 'user-desktop' not present in theme Ambiant-MATE (0)

Hi rosswmcgee I am sorry I got sidetracked yesterday:confused: 
I can see no real reason for mate-tweak not to start but I have seen where Themes can cause such errors, maybe change your theme along with changing icon theme as well to check...and just stabbing wildly here. but a purge of mate-tweak and a reinstall might help.
See this thread [http://ubuntuforums.org/showthread.php?t=2307437](http://ubuntuforums.org/showthread.php?t=2307437)
Sorry I have nothing relevant to offer here.:(

---

