---
title: "Menu items disappeared"
date: 2011-10-25
forum: Desktop Environments
---

### Post by AIR63 on 2011-10-25
Some menu items were lost, and reinstalling lubuntu didnt bring them back. 

How can I get my default start menu back?

Details:
Installed Lubuntu on 2 machines (upgrade from ubuntu 11.04.)
My "start menu" included (translated from danish) Graphics, Internet, Office, Sound and video, games, accessories, system tools, configuration, run, log out

After either an automatic lubuntu update OR using the regular ubuntu menu editor (by error)one computer lost some menu items and only has these left: Accessories, Games, Graphics, Internet, Office, Programming, Run, logout. NO system tools, no configuration.

Menu://Applications doesnt have the system group or configuration group.
/usr/share/applications include a users.desktop file (same on the system showing users in system tools group and the other system) but doesnt show the users menu entry.

I found the menu definitions once and they "all" contained a system tools group.

Not sure if the menu items are "suppressed" or deleted.
doenst help to add NoDisplay=false.

What are the mechanisms (files, commands...) that define the menu and how do I get it back to default?

---

