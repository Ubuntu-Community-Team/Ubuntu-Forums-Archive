---
title: "Firefox update and /usr/share/applications/firefox.desktop"
date: 2010-07-25
forum: Desktop Environments
---

### Post by LyeOnYou on 2010-07-25
Every time Firefox is updated it changes the /usr/share/applications/firefox.desktop so it uses the "firefox" icon instead of the one I manually changed.  It's very annoying because that ugly, oversized icon shows up when even the application window has a nice little Tango styled icon. Is there any way around this?

---

### Post by lovinglinux on 2010-07-25
Create your own desktop launcher for Firefox and add it to your panel. Works for me on KDE.

---

### Post by LyeOnYou on 2010-08-05
I think making the file immutable will prevent it from being messed with. I don't know why I didn't think of that earlier, but thanks for your quick reply.
```
chattr +i /usr/share/applications/firefox.desktop
```

---

