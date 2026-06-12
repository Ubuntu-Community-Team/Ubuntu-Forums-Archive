---
title: "Kchmviewer can't open files in nautilus with spaces in file name"
date: 2008-12-16
forum: Desktop Environments
---

### Post by jackhab on 2008-12-16
The problem is as described in the subject.
Nautilus launches Kchmviewer with file URI replacing the spaces in the file name with %20. Kchmviewer does not understand it.

I solved it by replacing
Exec=kchmviewer %U
with
Exec=kchmviewer %M
in /usr/share/applications/kchmviewer.desktop

Is this a bug? Whom should I report it to? Nautilus, Gnome, Kchmviewer?

---

