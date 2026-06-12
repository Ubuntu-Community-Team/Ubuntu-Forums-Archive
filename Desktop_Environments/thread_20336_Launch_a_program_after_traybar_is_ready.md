---
title: "Launch a program after traybar is ready"
date: 2005-03-16
forum: Desktop Environments
---

### Post by IdoMcFly on 2005-03-16
Hello!
I'd like to launch amule after the tray icone applet is ready because if it is not ready yet, amule create a window to put its tray icon.

How to do this?

---

### Post by IdoMcFly on 2005-03-18
[QUOTE=IdoMcFly]Hello!
I'd like to launch amule after the tray icone applet is ready because if it is not ready yet, amule create a window to put its tray icon.

How to do this?[/QUOTE]
 any idea?

---

### Post by ubuntu_demon on 2005-03-18
[QUOTE=IdoMcFly]any idea?[/QUOTE]
 try amule with order 60
does it work ?

---

### Post by cutOff on 2005-03-18
[QUOTE=IdoMcFly]Hello!
I'd like to launch amule after the tray icone applet is ready because if it is not ready yet, amule create a window to put its tray icon.

How to do this?[/QUOTE]
How do you install amule??

---

### Post by IdoMcFly on 2005-03-18
[QUOTE=demon666_nl]try amule with order 60
does it work ?[/QUOTE]
I already done this (I even tried 120...) but no success.

I've installed amule with aptitude

---

### Post by IdoMcFly on 2005-03-23
I've made an sh script launch_amule.sh 
```
#!/bin/sh
sleep 15; amule&

```

and put in ~/.gnomerc
```
launch_amule.sh&
```

it works, it's not really clean, but it works.

---

