---
title: "Font menu problems in some apps (LibreOffice,  pgAdmin, etc)."
date: 2013-11-01
forum: Desktop Environments
---

### Post by martinrame on 2013-11-01
Hi, since a couple of weeks I've been experiencing some problems (I think are) related to fonts in some apps, like LibreOffice and pgAdmin, as you can see in the attached screenshot, most menus aren't showing, as well as cell names.

Does anyone experienced this problem? any fix?.

I'm using Ubuntu 12.04 64bits - XFCE 4.10 - LibreOffice 4.1.2.3

[ATTACH=CONFIG]247454[/ATTACH]

---

### Post by martinrame on 2013-12-20
Iv'e found this behavior is related to the Compositor, when disabled everything works correctly.

Apart from font problems, one side effect of this compositor bug is that Cairo-Dock is launched many times when I first log-in. Look:

```
~  ps ax|grep cairo
 2670 ?        Sl     0:00 /usr/bin/cairo-dock
 2745 ?        Sl     0:00 cairo-dock
 2748 ?        Sl     0:00 cairo-dock
 2750 ?        Sl     0:00 cairo-dock
 2752 ?        Sl     0:01 cairo-dock
 2754 ?        Sl     0:00 cairo-dock
 2756 ?        Sl     0:00 cairo-dock
 2758 ?        Sl     0:00 cairo-dock
 2764 ?        Sl     0:00 cairo-dock
 2768 ?        Sl     0:00 cairo-dock
 2770 ?        Sl     0:00 cairo-dock

```

This doesn't happen when compositor if off.

---

### Post by bapoumba on 2013-12-21
Thanks for coming back to post the solution. Please mark your thread as Solved, in the "thread Tools" menu.

---

