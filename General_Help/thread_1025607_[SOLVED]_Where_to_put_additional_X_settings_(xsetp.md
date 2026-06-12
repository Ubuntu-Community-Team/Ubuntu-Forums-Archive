---
title: "[SOLVED] Where to put additional X settings (xsetpointer) ?"
date: 2008-12-30
forum: General Help
---

### Post by joehte on 2008-12-30
Hi,

for some strange reason my racing wheel is also controlling the mouse. This is quite annoying but can be fixed by running the following command:

```
xsetpointer -c  "Microsoft SideWinder Precision Racing Wheel USB version 1.0"
```

I don't want to run it every time I start the computer. I could put it into my startup scripts when I log in. But this is really a system wide setting so it should be for all users.

The problem is, I'm not quite sure what's the proper place to put it. I'd imagine it has to be run after X server has already started. I tried putting it into /etc/rc.local, but this did not work.

Anyone know how I can make this setting stick?

---

### Post by joehte on 2009-01-05
With some trial and error I found a place to put the command:

```
/etc/gdm/Init/Default
```

Put it before exit 0;

---

