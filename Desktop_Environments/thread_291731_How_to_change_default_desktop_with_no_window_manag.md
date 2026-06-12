---
title: "How to change default desktop with no window manager"
date: 2006-11-02
forum: Desktop Environments
---

### Post by ducriderx on 2006-11-02
I start up at run level 3 and have no desktop manager, KDM or GDM, but occasionally use X.

I want to change the default desktop to enlightenment from KDE when I run startx.  What changes do I need to make?

---

### Post by brentoboy on 2006-11-02
look in ~/.xinitrc

```

nano ~./xinitrc

```
that is the script that runs when you "startx"

does it even exist?

---

### Post by brentoboy on 2006-11-02
anyway,

if it doesnt exist, create it and add this line to it

```

exec enlightenment

```

if it does exist modify the "exec" command at the end to launch enlightenment instead of whatever is in there

---

