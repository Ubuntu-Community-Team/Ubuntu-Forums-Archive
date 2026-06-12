---
title: "Debian Menu appears in GNOME, but not Afterstep"
date: 2005-05-19
forum: Desktop Environments
---

### Post by DownloadTHIS on 2005-05-19
I added Afterstep the other day, and I was unhappy to learn that the debian menu is not appearing where it should. The "Debian" entry shows up, but there is nothing in it. How can I fix this?

---

### Post by jobezone on 2005-05-29
[QUOTE=DownloadTHIS]I added Afterstep the other day, and I was unhappy to learn that the debian menu is not appearing where it should. The "Debian" entry shows up, but there is nothing in it. How can I fix this?[/QUOTE]
 that's strange, see if there's an entry for afterstep in /etc/menus-methods . Perhaps AfterStep is just not supported because of it's age. You can read about the "menu" package in /usr/share/doc/menu/html/ ... but why are you using afterstep? Try WindowMaker which is much more developed and updated (and they have GnuStep which aims to clone Afterstep).

---

### Post by blackbeastofaarrgh on 2006-01-25
Left-click on desktop, choose the Desktop menu, click "update startmenu"
Worked for me.

---

