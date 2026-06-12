---
title: "Gnome3 restarts automaticly! Ubuntu 12.04"
date: 2012-05-24
forum: Desktop Environments
---

### Post by CProgramming on 2012-05-24
Hello everybody,
I have problem with gnome3 on Ubuntu 12.04

Version of gnome shell is 3.4.1 (don't require graphic acceleration ).

It's restarts the gnome shell by itself randomly. It's seems like a crash ..  I know that I'm not explaining myself good - but I believe that you know about that issue.

This wasn't happened on Ubuntu 11.10 (Maybe because that was gnome 3.2 who required graphic acceleration?)

Is there any solution or any workaround to this issue?

thanks!

---

### Post by CProgramming on 2012-05-25
Up..

---

### Post by markbl on 2012-05-25
Are you using the nvidia proprietary graphics driver? If so, search for nvidia and read about the xorg server crash bug in 12.04. X dies which you see as being dropped back to the login screen. Happens in any 3D desktop such as gnome-shell and Unity. Install either the nouveau driver or use a 2D desktop.

---

### Post by prokoudine on 2012-06-01
> **markbl said:**
> Are you using the nvidia proprietary graphics driver? If so, search for nvidia and read about the xorg server crash bug in 12.04. X dies which you see as being dropped back to the login screen. Happens in any 3D desktop such as gnome-shell and Unity. Install either the nouveau driver or use a 2D desktop.

Supposing I already use nouveau and still get random gnome-shell crashes?

---

