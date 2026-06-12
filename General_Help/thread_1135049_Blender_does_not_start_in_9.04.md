---
title: "Blender does not start in 9.04"
date: 2009-04-24
forum: General Help
---

### Post by Yumi on 2009-04-24
I installed Blender from the repositories. It fails to start with the following error:
```
$ blender
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  12
  Current serial number in output stream:  13
```
I do not know where to find Xlib or its extension GLX. Any help would be appreciated.

Michael

---

### Post by Menschenfresser on 2009-04-24
I think this means you need the appropriate drivers for your graphic card since it needs hardware supported acceleration to draw its GUI.

---

### Post by David C. on 2009-04-26
If you're running Blender 2.48 or less, you'll need Python 2.5 Blender won't operate on any Py version beyond 2.5. I tried it with Python 3.0 on XP. It didn't work, had to revert to 2.5

---

### Post by Tindytim on 2009-04-26
Apparently Blender from the Universe repositories is 2.48a. I know blender always gave me problems (regardless of what version of Blender or Ubuntu) when I didn't install my graphics drivers.

---

