---
title: "gnome doesn't load"
date: 2005-06-07
forum: Desktop Environments
---

### Post by mantasman on 2005-06-07
gnome doesn't load for me. linux core is running, i can login etc but gnome doesnt star automatically and when i write startx, i see only emty screen with mouse cursor system doesn't freeze.
i was downloading multimedia codecs before restart.
how can i fix this? what packages should i download?

---

### Post by blind0wl on 2005-06-21
Sounds like a fault with gdm or gnome is screwed.  Try restarting gdm with
```
/etc/init.d/gdm restart
```

If that doesnt work, when you startx, can you go back to the console Ctrl,Alt + F1 and see if there are any error messages appearing?

---

