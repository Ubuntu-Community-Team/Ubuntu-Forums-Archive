---
title: "installing xubuntu problem..."
date: 2006-09-17
forum: Desktop Environments
---

### Post by oldmanstan on 2006-09-17
i installed the xubuntu-desktop package and everything went fine except it didn't want to install the xfce terminal package, here's the error i get...

```
E: /var/cache/apt/archives/xfce4-terminal_0.2.5+r21674-0ubuntu2_i386.deb: trying to overwrite `/usr/bin/Terminal', which is also in package terminal.app
```

any suggestions? xfce ends up working just fine and all, it just uses the gnome terminal instead of its own. i'm just worried that i have a problem that should be fixed.

thanks

---

### Post by orb9220 on 2006-09-17
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by oldmanstan on 2006-09-17
i already did everything on that page, it's installed, it works, there's just a problem with apt, it doesn't want to install the xfce terminal app

---

### Post by kuja on 2006-09-17
Well, you could try to force install it. Or perhaps, you could also try figuring out what the other package is that includes that file and removing that package first. (the latter probably being the safer route)

---

