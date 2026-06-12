---
title: "Maximum Number of Clients"
date: 2013-05-16
forum: Desktop Environments
---

### Post by Gannin on 2013-05-16
Right now I'm using standard Ubuntu 12.10.  Often, after using my computer for about an hour, sometimes less, sometimes more, new programs won't open, and I get the error message:

```
Maximum number of clients reachedMaximum number of clients reachedError: cannot open display: :0
```

I haven't modified the system in any strange way.  I've just kept up with the regular system updates through the software updater, and I've kept my video card driver up-to-date.  This just started happening a couple weeks ago.

Out of curiosity, I then installed both LXDE and XFCE, and the same happens when using those DEs as well.

When this issue occurs, if I log out then log back in everything works again for another hour or so, but then the issue reoccurs.

Any ideas?

---

### Post by dino99 on 2013-05-17
its time to clean the system; specialy if you only do dist-upgrade and never install from scratch

clean/autoclean/autoremove/gtkorphan/bleachbit

---

