---
title: "firefox scrolling garbles text after xfce 4.2.1 upgrade."
date: 2005-03-29
forum: Desktop Environments
---

### Post by taygan on 2005-03-29
running ubuntu hoary, (xorg)

xfce 4.0 ran great. after upgrading to 4.2.1, when I scroll in firefox, many lines of text are cut off (as they scroll up).

tried metacity with xfce and it still happens, though seemingly not as bad.

neither xfwm4 nor metacity used with gnome 2.10 has this problem.

xcompmgr is not installed, so I assume there's no compositing going on.

HELP! xfce rocks, but firefox is becoming annoying.

---

### Post by taygan on 2005-03-29
AH HA! firefox bug, not xfce.

workaround:

Edit>Preferences>General>Fonts & Colors>Display Resolution

Change "from system setting" to 96 dpi, the lines/garbles go away.

---

