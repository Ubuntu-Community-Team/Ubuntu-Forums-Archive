---
title: "gconf-editor [Resolved]"
date: 2006-11-16
forum: Desktop Environments
---

### Post by gekkos on 2006-11-16
Hi,
I have a question.
With gconf-editor you can disable the hibernate button but only for the user using the gconf-editor. Is it possible to do this system wide so users can not hibernate the server anymore.
Many thanks,

---

### Post by mannheim on 2006-11-16
You can run gconf-editor as root ("gksudo gconf-editor"); then go to the File menu and select "New Defaults Window". Any changes you make there will effect the defaults for all users. You can also override other users' choices with "New Mandatory Window".

---

### Post by gekkos on 2006-11-16
Many thanks, that did it.

---

