---
title: "Unity2D Panel Broken (mouse over reverts to gnome-panel)"
date: 2011-05-17
forum: Desktop Environments
---

### Post by meist3r on 2011-05-17
So I just updated my IdeaPad to Natty and played around with Unity. The performane was absolutely unbearable so I installed Unity2D from the software center. Now when I start the session everything seems to be fine at first. Whenever I move the mouse over the panel though it seems to switch to my old gnome-panel from the "Classic" session (with some missing icons). When I move the mouse over that panel again it switches back to the Unity panel style. What is going on? Can I fix this somehow? I will have to use the classic session until I get a working consistent behavior :/

Any ideas. And yeah sorry, there are about a billion threads on Natty/Unity and I don't have the time to scan through all of them for possible clues. If you have any idea where to start I'd greatly appreciate it.

---

### Post by Krytarik on 2011-05-17
Check if Gnome Panel is actually running in that session:
```
ps ax |grep -v grep |grep gnome-panel
```
If so, make sure it is not set in "Startup Applications".

Greetings.

---

### Post by meist3r on 2011-05-17
That's pretty much the first thing I did but when I terminate the process (e.g. through System-Monitor) it automatically restarts gnome-panel just like it would under a "normal" Gnome session on panel crash. I'm way confused.

---

### Post by Krytarik on 2011-05-17
Ok, that's a good start.

I assume you are logging in to the session option "Unity 2D", since you referred to the "Ubuntu Classic" session options.

Try removing "panel" from the Gconf key "/desktop/gnome/session/required_components_list" in "gconf-editor".

If that doesn't fix it already, try removing the content of "~/.config/gnome-session/saved-session".

---

