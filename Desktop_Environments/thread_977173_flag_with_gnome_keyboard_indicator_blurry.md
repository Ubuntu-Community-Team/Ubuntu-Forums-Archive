---
title: "flag with gnome keyboard indicator blurry"
date: 2008-11-10
forum: Desktop Environments
---

### Post by eaidoido on 2008-11-10
I set my keyboard indicator to show flags, this works well, the only problem is that all the flags show up blurred/not sharp like the .pngs themselves. 

my panel height is 16 px and i have tried both 16 px and 24 px flag sizes with the same result. 

is there any way to adjust the scaling of these flag images for this applet? Thanks in advance

---

### Post by eaidoido on 2008-11-11
buuummp

---

### Post by gosualite on 2009-07-08
I have the same problem. I have tried various flags of different sizes but the panel seems to insist on slightly resizing it no matter what dimensions I guess, which blends the stripes in an ugly, nonuniform way. 

Does anyone know the exact dimensions the image should have to prevent the panel from wanting to resize it?

---

### Post by lorn on 2009-11-06
It's the bug in libgnomekbd. Fixed version is available in [author's PPA]("https://launchpad.net/~sergey-udaltsov/+archive/ppa").

In my case image height is 22px. PanelHeight&#8722;2px.

[IMG]http://lork.shell.tor.hu/store/flag-indicator.png[/IMG]
[IMG]http://lork.shell.tor.hu/store/ru-flag.png[/IMG]
[IMG]http://lork.shell.tor.hu/store/us-flag.png[/IMG]


[IMG]http://lork.shell.tor.hu/store/preview.png[/IMG]
[IMG]http://lork.shell.tor.hu/store/ru.png[/IMG]
[IMG]http://lork.shell.tor.hu/store/us.png[/IMG]

---

