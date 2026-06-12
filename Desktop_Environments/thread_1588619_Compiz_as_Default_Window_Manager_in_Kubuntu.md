---
title: "Compiz as Default Window Manager in Kubuntu"
date: 2010-10-05
forum: Desktop Environments
---

### Post by Shibblet on 2010-10-05
I'm trying to make Compiz activate at bootup, but I can't seem to get it to work.

Basically, I'd like to make Compiz the default Window Manager in Kubuntu Lucid.  Does anyone know how to accomplish this?

---

### Post by ankspo71 on 2010-10-05
Hi,
There are a few things you can try.

1. To change the default window manager (Kwin or Compiz) in KDE4.5+ go to:
Kmenu > System > System Settings > Default Applications > Window Manager > Use a different window manager.
KDE 4.4x may be a little different though.

2. If that doesn't work out, you can install "fusion-icon".  This gives you more control over which window manager and window decoration through an icon in the system tray.

3. You can also try to make a startup entry (or startup script). Try any of these lines of code to see what works best for you.
```
compiz --replace
compiz --replace && emerald --replace
emerald --replace
fusion-icon
```

---

