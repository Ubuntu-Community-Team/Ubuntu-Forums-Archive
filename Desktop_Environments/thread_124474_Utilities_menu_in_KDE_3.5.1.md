---
title: "Utilities menu in KDE 3.5.1"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Neo Ex on 2006-02-01
Hi. Today I've updated to KDE 3.5.1 but I have a (little) problem: the Utilities menu doesn't look like it did before: now it doesn't have submenus like Editors, Desktop etc. All programs now are in the Utilities menu without submenus.
Is there normal with KDE 3.5.1 or it's a bug? If it's a bug, how can I solve without using KMenuEdit (which I don't like very much)?
Thanks

---

### Post by gamma on 2006-02-02
That happened to me also. I'd try clearing out (probably back it up first) ~/.config/menus/applications-kmenuedit.menu and then restart kicker. That may fix it, if not that's probably the new default layout for KDE.

---

### Post by Neo Ex on 2006-02-02
Thank you, but I've just deleted that file and logged out and relogged in, but nothing changed.
Does somebody know how to fix this?
Thanks.

EDIT: I've tried deleting the .kde folder in my home (I've made a backup first :D), but the Utilities menu still doesn't have submenus. So I think that it is the new default layout of KDE 3.5.1.
We have to create the submenus with KMenuEdit, I think :(

---

