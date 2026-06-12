---
title: "Metacity &amp; dark Adwaita variant"
date: 2011-11-02
forum: Desktop Environments
---

### Post by gexi on 2011-11-02
As you may or may not know: Since 3.2, applications in gnome can make use of a dark theme variant. The only theme supporting this so far (at least I think so) is Adwaita. If you want to check it out you can just switch to Adwaita and start Totem or the default image viewer.

Well the problem is: this functionality is only implemented in Mutter yet. For unity, which uses compiz/metacity, the gtk-style will appear dark, but not the metacity window-borders.

Should I file a bug report for this, or is this by design?

---

### Post by crdlb on 2011-11-03
Yes, that is missing from metacity. I'm not sure if it can be done easily without a GTK3 port, and as far as I know that isn't planned. I don't know what compiz's plans are.

In any case, it's certainly worth filing a bug.

---

