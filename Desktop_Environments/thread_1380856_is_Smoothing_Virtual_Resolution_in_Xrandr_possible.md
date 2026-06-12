---
title: "is Smoothing Virtual Resolution in Xrandr possible?"
date: 2010-01-14
forum: Desktop Environments
---

### Post by mustafacolpan on 2010-01-14
i was trying 1920x1080 virtual resolution on my notebook display which has 1366x768 native resolution.

when i use this:
```

xrandr --output LCD --scale 1.405x1.405
```i get the first pic..


[IMG]http://img130.imageshack.us/img130/7251/xrandrlanczos.png[/IMG]

but in the same size, it is possible to see much better sharp and crisp fonts and icons. 

i wonder if there is a way to make it look like the second picture with xrandr or anything else? thanks!

---

### Post by mustafacolpan on 2010-01-15
i found a solution by my own but it is not perfect. advanced zoom function on compiz have a linear filter and it is exactly what i've wanted

but it requires a little tweak because it does not filter when it is full zoomed out. but i need it to keep filtering the screen when its full-frame desktop.

any ideas?

---

