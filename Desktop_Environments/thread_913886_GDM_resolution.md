---
title: "GDM resolution"
date: 2008-09-08
forum: Desktop Environments
---

### Post by mx. on 2008-09-08
How can I change resolution of the GDM login window? It's too large and I cannot the buttons which are at the bottom.

---

### Post by jis on 2009-02-09
You need a "Virtual" line in DISPLAY SUBSECTION of  xorg.conf. Type "man xorg.conf" in terminal for more help.

I wish you could change the resolution in Login window Preferences (that can be lauched by "gksu /usr/sbin/gdmsetup").

---

