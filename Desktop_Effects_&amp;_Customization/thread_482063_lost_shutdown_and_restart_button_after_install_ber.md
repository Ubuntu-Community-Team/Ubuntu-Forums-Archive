---
title: "lost shutdown and restart button after install beryl"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by oliviacond on 2007-06-23
i'm using kubuntu, fglrx, xgl.
i lost my shutdown and restart button after i install beryl.
only thing i got is logout button but this sometime works, sometime just give me a grey screen.
this is my startxgl.sh
```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec startkde
```

---

