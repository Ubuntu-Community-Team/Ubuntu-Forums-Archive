---
title: "kdm messes up dual-screen/xinerama?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by themoebius on 2006-07-13
For the longest time my kdm wasn't working so the computer would always boot into console and I would start gnome by typing startx. In those days my dual screen actually worked quite well. Programs were smart enough to start on one monitor or the other and not spread themselves across both screens, When I maximized a program it would maximize to that screen, the task bar would only  go across one screen. And, funny enough, I could use my keyboard shortcuts with amaroK even in Gnome. (Win + B to skip to next song)

Ever since I got kdm working again and starting Gnome through it, these nice features have stopped working.

---

### Post by themoebius on 2006-07-22
OK, its actually gdm as well as kdm. When I 're-break' my kdm and start gnome with startx the xinerama stuff works fine. Whats up with that?

I'm using the nvidia twin-view, which provides xinerama extentions, but I'm not using xinerama itself. perhaps that has something to do with it?

---

### Post by themoebius on 2006-07-22
I think the problem is due to Xgl/compiz actually. I didn't think about it because I'm not using a compiz enabled gnome session at the moment, but I guess Xgl is still running?

---

