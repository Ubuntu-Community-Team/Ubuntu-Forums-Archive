---
title: "Applications Menu Missing"
date: 2011-02-16
forum: Desktop Environments
---

### Post by omeganow on 2011-02-16
On 10.4 my applications, places, and system menu items no longer appear, after I made a change (do not remember exactly what I changed, unfortunately) to the screensaver settings and rebooted.

Tried to add the main menu item back to the menu  panel but it is grayed out in the Add Panel dialog.

How can I get the apps, places, etc. back?

---

### Post by jerrrys on 2011-02-16
do you have custom settings ?  if so, this will probably wipe them

but if not; open a terminal and

gconftool --recursive-unset /apps/panel && killall gnome-panel

---

### Post by omeganow on 2011-02-22
Thanks, got the  menus back, but not at the far left - Oh well.

---

### Post by Frogs Hair on 2011-02-22
Right click the menu icon or applications text and select move and put it where you want.

---

