---
title: "disable screensaver via terminal?"
date: 2007-05-13
forum: Desktop Environments
---

### Post by stinkinrich88 on 2007-05-13
Hello!!!!!

Is there a command I can use in the terminal to disable the screensaver and screen blanking!?

Thanks!

(i'm using Gnome, but other desktop environs would be useful too!)

---

### Post by stinkinrich88 on 2007-05-13
i've found an alternative solution now. But if anyone is interested, and are using gnome, use the following (with gconf-editor installed) to disable the screensaver. Use similar to disable screen blanking:



```
gconftool-2  --set "/apps/gnome-screensaver/idle_activation_enabled" --type boolean false
```

---

