---
title: "Can't modify the Kicker?"
date: 2007-03-04
forum: Desktop Environments
---

### Post by Kumagoro on 2007-03-04
I was just messing around on the liveCD (so i wont screw anything on the actual OS)

I tried to make a gnome-like two panels (top and bottom taskbar)

I made an additional panel, added proper applets to it and wanted to make it thinner.
So i went to the kicker settings and i could only modify the main kicker, not the added one. Below the monitor image there was nothing, hiwever when i did "what's this" it popped up that there are the panel lists (which was blank for me...)

How come?

---

### Post by Jucato on 2007-03-04
This is a bug in KDE. You need to restart kicker in order to "refresh" the list of available panels.

Press Alt+F2 and run this command:

```
dcop kicker kicker restart
```

---

