---
title: "Indicator applet icon location/name?"
date: 2023-07-31
forum: Desktop Environments
---

### Post by sienile on 2023-07-31
I'm having a hard time finding the location of the indicator applet menu on the Gnome panel (**not** the application menu, i.e. start-here.png). I've searched for everything I can think of, but none of the names I think would work match any of the icons used through my various themes. This is the menu icon that brings up the session options and lists help and settings. It's been a long time since I tried to mess with Ubuntu under the hood, but I swear this icon used to be with the rest in /usr/share/icons. Has it changed to a different location?

Doubt it matters, but I'm using Gnome Flashback. Ubuntu 22.04

Icon appears as a workstation here:
[IMG]https://i.imgur.com/yUSLQDB.png[/IMG]
[IMG]https://imgur.com/a/F5OWwtO[/IMG]

---

### Post by sienile on 2023-08-01
I've stumbled upon the answer here: [https://askubuntu.com/questions/208336/how-to-tweak-indicator-session-icon/209482#209482](https://askubuntu.com/questions/208336/how-to-tweak-indicator-session-icon/209482#209482)

The icon is [SIZE=3]system-devices-panel[/SIZE] (also system-devices-panel-information and system-devices-panel-alert) and I found it in the [SIZE=3]16x16/panel[/SIZE], [SIZE=3]22x22/panel[/SIZE], and [SIZE=3]24x24/panel[/SIZE] directories under the main icon theme directory (/usr/share/icons/*theme-name*/).

But some themes seem to not follow that naming convention and use [SIZE=3]system[/SIZE] in the [SIZE=3]*resolution*/devices[SIZE=2] directories. I can confirm that using the above icon name overrides this one.[/SIZE][/SIZE]

---

