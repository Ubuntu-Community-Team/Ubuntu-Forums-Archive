---
title: "Netbook optimized desktop"
date: 2009-05-09
forum: Desktop Environments
---

### Post by tarnis on 2009-05-09
Hi, I'm looking for some sort of suggestions on mofifying ubuntu for my s10e netbook.  It has a weird 1024x576 screen resolution that creates issues with several apps...Tried the nextbook remix and while the menu screen is nice it doesn't solve my problems as it kept the top panel...and the UI is flaky with the whole auto-maximizing thing.

In the end I'm looking to get rid of all of the panels.  I like crunchbang's menu system with the right click on desktop to bring up a menu or hit the superkey/Spacebar BUT don't like the having to manually edit the menu.xml file to update it and the configuration menus stink compared to ubuntu's.  I was curious if there was a similar way to set this up with a gnome menu and some screenlets for the battery life and whatnot but I don't see anything to replace the bottom panel window list...at least not in screenlets.    Autohiding the panel in Ubuntu robs me of a few precious verticle pixels so trying to avoid that.

Anyways, any thoughts?
Thanks,
Matt

---

### Post by ugm6hr on 2009-05-09
I think Gnome requires a panel.

XFCE panel-autohide actually hides the panel entirely.  Might be worth looking into.

---

### Post by Brandon Williams on 2009-05-09
With XFCE, you can turn the panel off entirely and get the menu with a right-click on the desktop. There are lots of different ways to gets icons on the desktop. Unfortunately, the version of XFCE in Jaunty doesn't have a menu editor any more, and maintaining a custom menu can be a pain.

FWIW, it looks like ubuntu has a package called obmenu, which provides a graphical menu editor for obenbox. That ought to be available for crunchbang as well, so if you like crunchbang, don't let menu editing keep you away from it. There's also an xdg menu converter that will take the standard gnome xdg-based menu and generate an openbox xml menu for you.

I seem to recall there being a way to get the main menu to pop up from the gnome desktop without requiring a panel, but I can't find a reference, so I must be imagining it. It is possible to run without the panel, though, so if you figure out another way to access the menu, then you can turn the panel off. Just navigate to the key /desktop/gnome/session/required_components_list in gconf-editor and remove panel from the list.

---

### Post by Brandon Williams on 2009-05-09
Unfortunately, the menu, the 'Run...' dialog, and the screenshot key all appear to be tied to the gnome panel, so disabling the panel altogether looks like a bad idea. However, you _can_ make it completely disappear.

In gconf-editor, set both /apps/panel/global/panel_minimized_size and /apps/panel/toplevels/top_panel_screen0/auto_hide_size (or bottom_panel_screen0, if that's where you're remaining panel is) to 0. Also, make sure that /apps/panel/toplevels/top_panel_screen0/auto_hide is true. Now, your panel will only take up one pixel of screen real-estate when hidden (I don't know why 0 doesn't mean 0, but OK).

You can get the menu to pop-up (which also unhides the panel) with <Alt>+F1, or you can change that to a different key (some like to use the Windows key for that). And if you were to enable screenlets of some sort (maybe the google ones?), you can toggle 'View Desktop' mode with Ctrl+Alt+D.

---

