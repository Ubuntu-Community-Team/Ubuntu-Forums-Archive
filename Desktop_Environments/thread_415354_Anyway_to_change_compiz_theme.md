---
title: "Anyway to change compiz theme?"
date: 2007-04-20
forum: Desktop Environments
---

### Post by b0ng0 on 2007-04-20
Hi, I have the desktop effects enabled in the settings but I was wondering if there is anyway to change the themes e.g. the window decorator. I know with beryl it uses emerald from when I used KDE, but I can't seem to find any options in ubuntu to select a theme.

Thansk

---

### Post by litemotiv on 2007-04-20
afaik beryl doesnt use the emerald window decorator specifically anymore either; you can just choose or install a different gnome theme and you&#314;l be good to go. ;)

(p.s., that be "System -> Preferences -> Theme")

---

### Post by mattymattysidebyeach on 2007-04-21
10-4, emerald is not necessarily called by compiz.

[INDENT][LIST]
[*]**which window decorator** is being used to draw your borders
[*]will dictate **what files will need to be edited**
[*]in order to give you the results that you are looking for
[/LIST][/INDENT]

assuming that you are using gnome with desktop-effects, its probably gtk-window-decorator that is being used.


knowing what flavor of compiz you have installed will help. at the command line, type in
[INDENT][I][B]apt-cache showpkg compiz
[/B][/I]
this will show you what compiz was installed, and which ones it required in order to be set up
[/INDENT]

from there you can determine where to go next

---

