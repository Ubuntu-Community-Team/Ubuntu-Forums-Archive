---
title: "windows list applet does not follow icon theme for certain applications"
date: 2011-03-30
forum: Desktop Environments
---

### Post by xeptf4 on 2011-03-30
Hi,
I am using Faenza Icons, which is reflected in the icons on the throughout the system except in the windows list applet for certain applications like Firefox and Chrome in the gnome panel. The indicator applet and the menu do show Faenza icons for all the items (including firefox and chrome). I am yet to check for other applications which do not follow the icon theme.

Can this be rectified? I want the windows list to be consistent with the menu and it feels strange that certain applications follow their own icons disregarding the theme I have selected.

---

### Post by Copper Bezel on 2011-03-30
There's sometimes a default icon associated with the application itself that doesn't come with the theme, I think just referred to as the "application-specified icon," that isn't overridden by icon settings in all contexts. Compiz reads this icon, too, so it's not specific to Gnome Panel, and there are other applications that do this, like (somewhat ironically, given your list) Opera. I don't know of any way to rectify this, though.

There's DockBar, which is an alternate application switcher for Gnome Panel that doesn't read the application-specified icon, but the behavior is different from the normal application switcher (more like Windows 7's Superbar) and it might not suit your tastes.

---

