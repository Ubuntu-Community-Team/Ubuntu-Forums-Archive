---
title: "Performance loss when using XFCE (or whatever) compared to GNOME"
date: 2007-03-01
forum: Desktop Environments
---

### Post by malfist on 2007-03-01
I recently switched my desktop to Xubuntu from ubuntu and have noticed a loss in performance. I have 3 128MN memory chips and a PIII 450MHz processor. When in GNOME firefox loads slowly but in XFCE it seems to load even slower. I haven't timed it yet, it's just apporoximation but it seems to me that XFCE loads slower than GNOME.

Any explanations? Any performance tips?

---

### Post by kalikiana on 2007-03-01
How did you 'switch' to XFCE? Is it a completely fresh install? Normally XFCE should perform much faster than Gnome. So some more details would be helpful to understand your specific situation.

---

### Post by sjnovick on 2007-03-01
My guess is this:

If you use a GNOME-based application within XFCE, then you need to load all of the GNOME libraries needed for that piece of software.  It may be true that most or all of the libraries are already loaded when you're using GNOME as your GUI, but not loaded when you use XFCE as your GUI.  I believe the whole idea behind XFCE is to use non-GNOME/non-KDE applications wherever possible.

---

### Post by malfist on 2007-03-01
No it's not a fresh install, I switched by logging out and set XFCE to defualt session. I do not believe firefox is either KDE or GNOME. Maybe it's where I haven't restarted it sense doing that.

---

