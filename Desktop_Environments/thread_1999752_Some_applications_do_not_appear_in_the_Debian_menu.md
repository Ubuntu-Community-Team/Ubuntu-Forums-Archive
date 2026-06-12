---
title: "Some applications do not appear in the Debian menu"
date: 2012-06-08
forum: Desktop Environments
---

### Post by Gullible Jones on 2012-06-08
I've noticed that, if the 'menu' package is installed, some installed applications never appear in the Debian menu. Firefox never appears anywhere in it, for instance. Running 'update-menus' (as root) does not help.

I've also read that [here](https://launchpad.net/ubuntu/+source/firefox/11.0~b1+build1-0ubuntu1) that Firefox's Debian menu entry has been dropped as "obsolete." Presumably that also applies to various other applications.

What can I do to make these applications show up? I'd rather not resort to editing my window manager's menus manually.

---

### Post by Gullible Jones on 2012-06-17
So, after some Googling I installed the menu-xdg package and ran update-menus as root... That did nothing at all. Many applications with .desktop files are still not shown in the Debian menu... In fact the menu's contents have not changed at all. What's going on here?

---

