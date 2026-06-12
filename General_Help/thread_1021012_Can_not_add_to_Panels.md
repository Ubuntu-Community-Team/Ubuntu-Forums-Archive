---
title: "Can not add to Panels"
date: 2008-12-24
forum: General Help
---

### Post by ephman on 2008-12-24
hi,

i'm running 8.10 off a fresh install.  for some reason out of the blue when i right click on a panel i do not get the option to add anything to it. only help and about panels shows. any ideas would be great.

thanks,

ephman

---

### Post by hailukah on 2008-12-24
Your panel has been locked.

Press Alt-F2 to bring up the run dialog and type gconf-editor.  Navigate to apps > panel > global and uncheck locked_down.  That should fix it.

---

### Post by ephman on 2008-12-25
that was it!  thanks.

ephman

---

