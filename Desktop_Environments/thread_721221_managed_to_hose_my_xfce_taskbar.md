---
title: "managed to hose my xfce taskbar"
date: 2008-03-11
forum: Desktop Environments
---

### Post by edroid on 2008-03-11
I've just installed Xubuntu, so everything is pretty much default
settings.  I wanted to see if the taskbar (bottom) could be made to
slide in/out as can be done in Gnome.

A right-click brought up the Panel Manager.  I tried changeing from
"Fixed Position" to "Freely Moveable" which shortened the task bar
considerably and centered it.  I tried undoing this by switching back
to "Fixed Position", but was unable to restore it.

As I tried to fix this, it got rapidly worse - leaving me with no
taskbar at all - just 3 small white rectangles scattered about the
screen!

Is there a way to restore this or do I need to reinstall?

---

### Post by sisco311 on 2008-03-11
To restore the default panels open a terminal and delete the ~/.config/xfce4/panel directory:
```
rm -rf ~/.config/xfce4/panel
```

```
killall xfce4-panel
```

press Alt+F2 and run: xfce4-panel

---

### Post by edroid on 2008-03-11
Excellent!  Thank you sisco311 !  You are a real guru.

---

