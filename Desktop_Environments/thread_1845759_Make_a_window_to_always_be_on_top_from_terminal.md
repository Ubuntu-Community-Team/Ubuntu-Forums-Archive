---
title: "Make a window to always be on top from terminal"
date: 2011-09-17
forum: Desktop Environments
---

### Post by Trubbelgum on 2011-09-17
Hi! Is there any command to make a window to "Always stay on top" from terminal.
I'm asking because of a script I'm making, where I want firefox to always be on top.

I want it to be like this:
```
firefox http://www.ubuntu.com/ -"Always stay on top"
```

---

### Post by Frogs Hair on 2011-09-17
If you use Compiz as your window manager and have the CCSM installed you may want to look at the window rules option . That may point you in the right direction .

---

### Post by Copper Bezel on 2011-09-17
I don't know if this helps, but for a *currently-running *window, you can do this:

```
wmctrl -r [window title] -b add,above
```

---

### Post by bioterror on 2011-09-17
iFail, I look totally wrong the section.
Sorry ;)

---

