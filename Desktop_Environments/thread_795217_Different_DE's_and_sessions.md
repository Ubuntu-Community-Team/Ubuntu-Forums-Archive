---
title: "Different DE's and sessions"
date: 2008-05-15
forum: Desktop Environments
---

### Post by boyce1 on 2008-05-15
Is it possible to have more than one desktop enviroment? i see on the login screen, you can chose Gnome from the session, so am i right in thinking you can install another desktop environment?

I've heard a bit about Xfce, and wanted to try it out. would this mean removing gnome and installing xfce, or can i have them both and switch?

 thanks.

---

### Post by Nepherte on 2008-05-15
Yes, you can install them. By default your other environments won't be removed. You can then select the environment you want in the login screen.

To install XFCE:
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by Xiong Chiamiov on 2008-05-17
That will install all of the packages associated with it as well, just as if you installed Xubuntu directly.  If you just want XFCE itself you can run
```

sudo aptitude install xfce

```

---

