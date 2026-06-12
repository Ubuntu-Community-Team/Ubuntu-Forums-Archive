---
title: "&quot;Full Screen&quot; and Maximized windows appear outside the frame buffer size"
date: 2015-05-28
forum: Desktop Environments
---

### Post by Rumpkie on 2015-05-28
I am running lubuntu 14.04 and have an HDMI port setup to deal with HDMI overscan
```
xrandr --output HDMI1 --mode 1920x1080 --fb 1920x1080 --transform 1.06,0,-60,0,1.06,-60,0,0,1
``` 
it says:
```
xrandr: specified screen 1920x1080 not large enough for output HDMI1 (2036x1145+-60+-60)
```

the system does exactly what I want it to do, creates a 6% scaled down 1920x1080 desktop frame buffer in the middleish of a 1920x1080 signal
but now when I maximize a window inside the desktop environment it maximized to 2036x1145 not the frame buffer's 1920x1080.
please help,
-Cory

---

