---
title: "Unruly panels"
date: 2011-11-16
forum: Desktop Environments
---

### Post by The Eight-Bit Link on 2011-11-16
I upgraded to the gnome 2 panels from Unity, but they don't seem to work correctly. For one, they don't have a settings menu, nor can I move/modify the apps in the panel. Help please?

---

### Post by Copper Bezel on 2011-11-17
If you have the package compizconfig-settings-manager installed, you can change some settings for the Unity launcher and Panel in the Unity plugin in the CompizConfig interface. However, they're designed to work in a specific, integrated way* and can't be modified in the way you're used to with the old Gnome panels.

You can add running applications to the Launcher or remove them by right-clicking the icons themselves. To reorder the icons, grab them and move them slightly to the right, out of the launcher, then back in where you'd like to drop them.

*A couple of examples: Dragging and dropping a file from the file manager automatically unhides the Launcher panel, so that you can drop the file onto a waiting application launcher, which will be lit if it supports the mimetype; opening an application menu from the keyboard (such as by Alt+F) and cycling with the arrow key will eventually get you into the system tray items, because the menu and system tray are all treated as one big menu bar; the Workspace Switcher doesn't draw the area of the screen covered by the top panel or, if the Launcher isn't set to autohide, the area covered by the Launcher. All of these tweaks depend on a specified arrangement for the panel objects.

---

### Post by robert shearer on 2011-11-17
perhaps the o/p has moved to gnome-session-fallback which **looks** like gnome2 but is Gnome3 and has some different configuration options...

1) **alt+right-click** on a panel to be able to customise, move, etc (old gnome2 behaviour was right-click only)

2)Settings are under Applications>System tools>System settings and Applications>Other

Post again if you need help from here...

---

### Post by Copper Bezel on 2011-11-17
Ah. I misread "Gnome 2 panels" as "Gnome with two panels" instead of  "Gnome version 2 panels" and "from Unity" as "provided by Unity" instead of "as opposed to Unity." Thanks for spotting that. = )

---

