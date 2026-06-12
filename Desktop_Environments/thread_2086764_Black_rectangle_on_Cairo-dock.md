---
title: "Black rectangle on Cairo-dock?"
date: 2012-11-21
forum: Desktop Environments
---

### Post by Ragi1992 on 2012-11-21
I have Cairo-Dock (NO OpenGL)
and GLX-Dock (Cairo-Dock with OpenGL)

I installed compiz on Synaptic Package Manager (like it told me to do to get rid of rectangle)
its telling me something about compositing not being turned on.

What do I need to do to get this black rectangle off? And how do I turn compositing on? And also when I restart my computer it goes back to original toolbar.

I am running Lubuntu 12.04

Any help appreciated! Also I am a rather new Unix computer user

---

### Post by zombifier25 on 2012-11-22
You need to run Compiz for LXDE in order to use compositing. Run this command:
```
compiz --replace
```
If you want, then you can add it to startup applications. Though I'm sure there's a much more efficient way to do this than manually killing LXDE's window manager every time to replace it with Compiz.

NOTE: When you run Compiz, it may not work completely the first time. You should install compizconfig-settings-manager first, and enable the needed plugins (Composite, Windows Decoration, Resize Window, Move Window, etc.)

---

