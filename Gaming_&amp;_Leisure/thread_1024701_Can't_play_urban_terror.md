---
title: "Can't play urban terror"
date: 2008-12-29
forum: Gaming &amp; Leisure
---

### Post by Knark on 2008-12-29
Every time i try to start it, it says "cannot display this video mode, optimum resolution 1280x1024 60 Hz" I use ubuntu intrepid

---

### Post by ubersolid on 2008-12-30
> **Knark said:**
> Every time i try to start it, it says "cannot display this video mode, optimum resolution 1280x1024 60 Hz" I use ubuntu intrepid

Open up ~/.q3a/q3ut4/q3config.cfg

```
nano ~/.q3a/q3ut4/q3config.cfg
```

look for
```
seta r_fullscreen "1"
```
and change that to 0

When you start the game it will be in windowed mode, and you can set it back to fullscreen using your preferred resolution using the game menus.
If it fails, back out using ESC a couple of times, and start the game again, sometimes it takes a while for the setting to take effect...

---

### Post by Knark on 2009-01-03
that works perfectly thanks

---

