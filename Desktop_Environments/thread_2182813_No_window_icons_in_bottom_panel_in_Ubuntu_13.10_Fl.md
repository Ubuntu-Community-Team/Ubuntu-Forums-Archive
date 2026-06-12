---
title: "No window icons in bottom panel in Ubuntu 13.10 Flashback after changing screen res."
date: 2013-10-22
forum: Desktop Environments
---

### Post by kjellahl on 2013-10-22
I used to use the Ubuntu Gnome Fallback desktop, which was replaced by Gnome Flashback when I upgraded from Ubuntu 13.04 to 13.10.

After the upgrade to 13.10, the top and bottom panels don't change their length when I change screen resolution. And what is worse, the icons showing running applications disappear from the bottom panel. When I have minimized a window, I can't easily restore it.

I have a laptop with an internal display. Often I have an external display connected to it, which can be set to a higher resolution (1920 x 1080, compared to 1366 x 768 for the internal display).

I've defined two keyboard shortcuts for switching between these displays and resolutions with the commands

xrandr --output LVDS --auto --output VGA-0 --off
and
xrandr --output LVDS --off --output VGA-0 --auto

This worked well in Ubuntu 13.04, but in 13.10 the top and bottom panels don't react properly to a change of resolution. They look fine when I log in, and adapt correctly to the resolution that I've selected in the System Settings - Displays dialog. But when I change resolution, either in the System Settings dialog or with an *xrandr* command, the window icons disappear from the bottom panel. They reappear when I change back to the log-in resolution.

What can I do to make the top and bottom panels react correctly to a change in screen resolution?

---

### Post by kjellahl on 2013-10-27
It's probably a bug in gnome-panel. See the bug reports
[https://bugzilla.gnome.org/show_bug.cgi?id=704622](https://bugzilla.gnome.org/show_bug.cgi?id=704622)
[https://bugzilla.gnome.org/show_bug.cgi?id=709549](https://bugzilla.gnome.org/show_bug.cgi?id=709549)

---

