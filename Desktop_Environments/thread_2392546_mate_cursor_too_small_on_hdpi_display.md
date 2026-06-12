---
title: "mate cursor too small on hdpi display"
date: 2018-05-22
forum: Desktop Environments
---

### Post by ajgreeny on 2018-05-22
This is driving my wife, and consequently me, mad as the mouse cursor in Ubuntu-Mate 18.04 is so tiny that it is almost invisible.

How can this be enlarged?
A new theme, and if so anybody got any recommendations?

EDIT:
Nevermind.
I have been searching all afternoon but didn't find how, then stumbled on the way.
Install dconf-tools which also adds dconf-editor.
Open dconf-editor from System tools menu and go to **org/mate/desktop/peripherals/mouse/cursor size** and set to one of the available sizes; 24 is default but 32 and 48 are also available for the mate cursor.

---

