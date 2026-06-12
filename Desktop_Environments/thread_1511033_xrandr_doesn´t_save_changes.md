---
title: "xrandr doesn´t save changes"
date: 2010-06-16
forum: Desktop Environments
---

### Post by netlord on 2010-06-16
hi forum

i have an little problem with xrandr.
my mediacenter is attached to an beamer with the optimal resolution of 1280*720
ubuntu 10.04 doesn´t offer me this revolution (on my intel 915 graphis controller).
this means i have to add this resolution to the possible resolutions.
first i used cvt
```
cvt 1280 720 60 
```
and got this result:
> # 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
then i added this to xrandr
```
xrandr --verbose --newmode "1280x720" 74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```
and
```
xrandr --verbose --addmode VGA1 1280x720
```

now i can select and use the new resolution - until next reboot.
after an reboot 1280x720 is again not available.
even if i work with sudo - the resolution isn´t there....

what i´m doin wrong?

thanks
netlord

---

### Post by Fsmv on 2010-06-19
I had the same problem except that I just want to change the primary screen and the position. There's probably a better way but I just made a small script run on startup. Mine is just two lines:
```

#!/bin/bash

xrandr --output HDMI-0 --primary --pos 0x60

```But your's would be:
```

#!/bin/bash

xrandr --verbose --newmode "1280x720" 74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync

xrandr --verbose --addmode VGA1 1280x720

xrandr --output VGA1 --mode 1280x720

```

---

