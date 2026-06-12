---
title: "KDE: Can't edit the Kmenu"
date: 2007-09-09
forum: Desktop Environments
---

### Post by daller on 2007-09-09
Hi there,

Just installed Gutsy Tribe 5, and dist-upgraded!

I have a problem with the Kmenu;

If I try to save changes in "KDE Menueditor" I get this message:
```

The menuchanges could not be saved because of the following problem:

Couldn't write to: /home/lea/.config/menus/applications-kmenuedit.menu
```

...translated from Danish, that is!

The only content of "/home/lea/.config/" is a file called "Trolltech.conf"

SOLUTION:

I created the folder 
"menus", and the file "applications-kmenuedit.menu" (by root), and changed the priviledges of the file.

---

### Post by kellemes on 2007-09-10
Seems to be a bug.
[https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/88426]("https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/88426")

---

