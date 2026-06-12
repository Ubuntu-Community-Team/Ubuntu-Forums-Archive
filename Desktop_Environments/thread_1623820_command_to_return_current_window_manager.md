---
title: "command to return current window manager"
date: 2010-11-17
forum: Desktop Environments
---

### Post by bluIT on 2010-11-17
I am looking for a command to return the current window manager. The reason I am looking at writing a simple script like thing that easily switches between compiz and metacity for running games.
P.S. not sure if "window manager" is the right reference. want to write something like

if "window manager = compiz
  metacity --replace
else
  compiz --replace

Hope that makes sense

---

### Post by stinkeye on 2010-11-17
You could use 
```
wmctrl -m | grep "Name:" | awk '{print $2}'
```
You may need to install **wmctrl**.

---

### Post by bluIT on 2010-11-17
Cheers bud worked like a charm

---

