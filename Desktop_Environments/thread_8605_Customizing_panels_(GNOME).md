---
title: "Customizing panels? (GNOME)"
date: 2004-12-19
forum: Desktop Environments
---

### Post by ReiKn on 2004-12-19
I can't find a way to customize panels in GNOME. 

> GNOME 2.8 Desktop User Guide
-10.2 Where to Find Preference Tools:
*Panel preferences* Applications -> Desktop Preferences -> Advanced -> Panel

First, there isn't such menu as "Advanced". Ok, I found it via nautilus with preferences:/// but there are only links to "CD Database Server", "Login Photo" and "Multimedia Systems Selektor".

I would like to be able to do customizations found in the User guide under "11.13 Customizing Your Panels". I have just installed Ubuntu so I haven't removed anything...

---

### Post by tomchuk on 2004-12-19
Those seem to be generic Gnome instructions - Ubuntu uses a slightly tweaked (for the better) Gnome, especially regarding menus. Most of the desktop configuration can be reached from Computer->Desktop Preferences. You can also set some preferences fror the panel by right-clicking it and choosing preferences.

If you're after more configuration options you can use gconf editor (Applications->System Tools->Configuration Editor) and go to /apps/panel/global which will give you the configuration options that are listed under the user guide.

---

### Post by ReiKn on 2004-12-19
[QUOTE=tomchuk]
If you're after more configuration options you can use gconf editor (Applications->System Tools->Configuration Editor) and go to /apps/panel/global which will give you the configuration options that are listed under the user guide.[/QUOTE]

Thanks. This helped, although I found the settings I wanted under /apps/panel/toplevels.

---

