---
title: "KUbuntu 13.04 Plasma Desktop Boder Rendering Problem"
date: 2013-05-31
forum: Desktop Environments
---

### Post by prosp4300 on 2013-05-31
Hi, All

After I upgrade to 13.04, my KUbuntu Plasma Desktop have problem to render boders, please see following attached screenshots

There always some white wrong border, and the corner is not aligned properly

Please let me know if there is any idea to fix it, any package I missed to install or some configuration related problem

[ATTACH=CONFIG]243336[/ATTACH][ATTACH=CONFIG]243335[/ATTACH][ATTACH=CONFIG]243337[/ATTACH]

Appreciate you help

---

### Post by Erik1984 on 2013-05-31
Maybe an issue with the video drivers, do you have a GPU which requires proprietary drivers? Are they installed?

Other things you could try:
- Try another theme (settings -> workspace appearance -> desktop theme)
- Change Kwins compositing to Xrender instead of OpenGL (settings -> desktop effects -> advanced tab -> compositing type)
- Create a new user and log in as that new user and add the same widgets, see if they appear correct there. I mention this because if you create a new user you start with fresh KDE settings.

---

### Post by prosp4300 on 2013-06-01
Thank you very much for your great suggestion

It is a desktop theme problem, only happen for Air theme, once change it to others, the problem gone

---

