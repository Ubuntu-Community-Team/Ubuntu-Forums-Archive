---
title: "xgl screen blanking"
date: 2006-10-27
forum: Desktop Environments
---

### Post by Charles Hand on 2006-10-27
Running xgl, after about fifteen minutes, the screen goes black. When there is a keyboard/mouse event the screen returns to normal.

There is no screensaver running, and the power settings are set to never turn off the monitor.

I have the option of running an xgl session or a non-xgl session. When I run a non-xgl session, this screen blanking doesn't happen.

/usr/bin/startxgl.sh:
```

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
DISPLAY=:1
exec gnome-session


```

---

### Post by CarpKing on 2006-10-27
I experience this as well.  I think it's just the screensaver, only xgl interferes with its functioning the same way it interferes with some other programs that use OpenGL (every once in awhile I'll see an actual screensaver, and it's always the ones that don't have any 3D effects).  Nothing to worry about as far as I can tell, but it is one of those little things that makes me wish for the day when xgl is unnecessary.

---

