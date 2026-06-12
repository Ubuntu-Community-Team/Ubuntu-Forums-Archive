---
title: "where is the gnome-timer-applet ?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by leafw on 2007-05-05
After installing the homonimous package, the "Installed Files" in synaptic don't list any binary for it. Where is it? It was working fine in Edgy.

---

### Post by meonkeys on 2007-12-30
> **leafw said:**
> After installing the homonimous package, the "Installed Files" in synaptic don't list any binary for it. Where is it? It was working fine in Edgy.

The "timer-applet" package might be what you're looking for. I found this using the following command line:

```
$ apt-cache search timer | grep -i gnome
timer-applet - timer applet - a countdown timer applet for the GNOME panel
```

What's "homonimous"?

---

