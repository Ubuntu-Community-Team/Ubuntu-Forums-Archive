---
title: "Creating/Modifying Panels using Command Line"
date: 2008-04-08
forum: Desktop Effects &amp; Customization
---

### Post by nuclearpidgeon on 2008-04-08
Hi

Is there any way to create or modify Panels for GNOME using a command in terminal? I am using Mac4Lin and have made 2 scripts to switch between metacity (ubuntu human) and compiz (Mac4Lin). See, I use avant-window-navigator for my window list, so If I could make it so that when I run the script, it creates a panel to put the apps on. Or perhaps just mod the top one to add a window list. I thought of using config files or the like for the panels then modifying them somehow (echo?), but I couldn't find them in the first place. I also want to change the background colour of the top panel (from transparent grey (leopard) to system default for ubuntu human).

Here are my current 2 scripts:

METACITY
#!/bin/bash
killall avant-window-navigator
gconftool --type string --set /apps/metacity/general/theme "Human"
gconftool --type string --set /desktop/gnome/interface/gtk_theme "Human"
gconftool --type string --set /desktop/gnome/interface/icon_theme "Human"
metacity --replace

COMPIZ
#!/bin/bash
gconftool --type string --set /apps/metacity/general/theme "Mac4Lin_GTK_Aqua_v0.3"
gconftool --type string --set /desktop/gnome/interface/gtk_theme "Mac4Lin_GTK_Aqua_v0.3"
gconftool --type string --set /desktop/gnome/interface/icon_theme "Mac4Lin_Icons_v0.3a"
compiz --replace
killall emerald
emerald
avant-window-navigator

P.S.
As a extra note, does anyone think that it might be worth making a how-to for this, as I am keen to make one :).

---

### Post by insineratehymn on 2008-04-08
Don't know how to do it... but yes. I would love to see a how-to.

---

### Post by nuclearpidgeon on 2008-04-09
started how-to:
[http://ubuntuforums.org/showthread.php?p=4682270](http://ubuntuforums.org/showthread.php?p=4682270)

---

