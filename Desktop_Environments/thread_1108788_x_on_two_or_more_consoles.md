---
title: "x on two or more consoles"
date: 2009-03-28
forum: Desktop Environments
---

### Post by mashada on 2009-03-28
Hi,

just wanted to know if possible to run x-GUI on two or more consoles (as the same user).
When i have gnome running, switch to a console and type: startx , it gives me an "fatal error" message, saying its "already in use on display 0".

Regards

---

### Post by stderr on 2009-03-28
Hi mashada; welcome.

You'll want to set the display to one higher than 0 (the default).

Ctrl+Alt+F7 takes you to xserver display 0
Ctrl+Alt+F8 takes you to xserver display 1
etc

So, to start a second xserver you could use

```
startx -- :1
```

and to start a third,

```
startx -- :2
```
etc.

Although I haven't experienced brilliant stability with multiple xservers in ubuntu before, things may have improved by now.

---

