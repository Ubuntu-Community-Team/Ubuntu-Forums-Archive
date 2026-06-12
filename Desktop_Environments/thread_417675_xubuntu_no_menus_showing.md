---
title: "xubuntu no menus showing"
date: 2007-04-21
forum: Desktop Environments
---

### Post by eier on 2007-04-21
i've just installed xubuntu 7.04 on a old computer the innstallation went without problems,
but when i start it no menu is showing.
i have the desktop icons and can right click and access then menus, but it's not showing in the bottom of the screen and in the top of the screen.
when it starts up i get this: unable to locate rsdp
tried the live cd on an newer computer and the menus popped up.
the computer:
intel pentium pro
256mb ram
matrox millenium g200

anyone have any ideas??

---

### Post by john.nicholls on 2007-04-22
Can you right-click on a blank area of the panel, select add new item, and add the menu that way?

---

### Post by eier on 2007-04-22
i dont have that panel... it's just the icons and pointer on my screen:(

---

### Post by john.nicholls on 2007-04-22
If you type
```
xfce-setting-show
```
you will get the settings manager and can make any adjustments (including installing one or more panels) from there.

---

### Post by FuturePilot on 2007-04-22
Try this <Alt><F2> then type in ```
xfce4-panel
``` That should start the panel. I'm not sure why it's not starting when you login though.

---

