---
title: "craziest question ever????"
date: 2005-03-26
forum: Desktop Environments
---

### Post by blinksilver on 2005-03-26
okay here it is, is there anyway to hardwire gnome to knoqueror, and i don't mean just install it and run it (already doing it), i mean replace nautilus with konqueror

---

### Post by cwaldbieser on 2005-03-26
I am not sure exactly what level of integration you are expecting, but you could always just remove nautilus, and do a

```
$ sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
```

I haven't actually tried this, but any program that tries to launch nautilus should launch konqueror instead.

Of course, some behavior specific stuff is still controlled by the KDE desktop settings rather than your Gnome desktop settings.

---

### Post by out of the blue on 2005-03-26
Even if you did this, you would still run into problems with launching gnome preferences, etc, since it uses nautilus-specific URIs.

---

### Post by blinksilver on 2005-03-26
i see what you mean, my biggest concern is memory, alot of nautilus stuff starts at startup, konq is pretty big, and don't want them both on startup

---

