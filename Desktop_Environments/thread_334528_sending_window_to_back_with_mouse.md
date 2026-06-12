---
title: "sending window to back with mouse"
date: 2007-01-09
forum: Desktop Environments
---

### Post by linusl on 2007-01-09
Hello, I recently installed ubuntu and i am using gnome (metacity).
I notice that when I middleclick a windows titlebar, the window is sent to the back. I am however used to performing this action with a rightclick on the titlebar. Is there anyway I can use a rightclick instead of a middle click on a windows titlebar to send it to the back?

I have not found any settings for this (I have looked in the usual menus, and in gconf-editor). I also used beryl for a while, and found no related settings there either (don't know if beryl and metacity uses the same settings for this). Is there some hidden file I can edit, och some program I can use?

---

### Post by tweedledee on 2007-01-09
> **linusl said:**
> Hello, I recently installed ubuntu and i am using gnome (metacity).
I notice that when I middleclick a windows titlebar, the window is sent to the back. I am however used to performing this action with a rightclick on the titlebar. Is there anyway I can use a rightclick instead of a middle click on a windows titlebar to send it to the back?

I have not found any settings for this (I have looked in the usual menus, and in gconf-editor). I also used beryl for a while, and found no related settings there either (don't know if beryl and metacity uses the same settings for this). Is there some hidden file I can edit, och some program I can use?

Not with metacity - the settings in gconf-editor are pretty much it.  You can install another window manager, though; I'm not sure which onse would enable this behavior, but it's fairly easy to try different window managers and see which one you like.  A simple replacement that integrates fairly well with Gnome is xfwm, the window manager from XFCE (works independently of the rest of XFCE).  Fluxbox, etc. may also work.

---

