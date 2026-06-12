---
title: "Weird font rendering - Unity 2D 12.04 Radiance theme"
date: 2012-05-01
forum: Desktop Environments
---

### Post by dakukuu on 2012-05-01
I don't know if this has already been posted but I have had this issue before in 11.10. Does anyone know how to solve this problem? It seems to only occur with the radiance theme, and mainly on unity 2D. My graphics card is Intel Mobile Chipset 4 series.

[IMG]http://i45.tinypic.com/24xi3wj.png[/IMG]

Thank you for any help. This is not a major issue, just an inconvinience. I usually use Gnome-Fallback anyway.

EDIT: Just tested in Gnome-Fallback, it definately appears correctly so I presume this is a Unity2D bug. I have to sleep now so I will check this thread tomorrow.

---

### Post by wout25 on 2012-05-02
same here:

radiance theme
unity 2D
Intel GMA3150

No problems in 11.10

Hope this gets fixed,
w.

---

### Post by NotSoTangible on 2012-05-04
[Bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/986865")

Comment #6 did the trick for me:
Install MyUnity, it will then be available under System settings 
Choose the "Font" tab, change "Antialiasing" to "grayscale" and close MyUnity
Enjoy!

---

