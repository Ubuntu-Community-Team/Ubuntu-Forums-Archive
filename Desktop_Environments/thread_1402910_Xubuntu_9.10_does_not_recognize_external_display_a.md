---
title: "Xubuntu 9.10 does not recognize external display and ugly login screen..."
date: 2010-02-09
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-09
Hi,
i have dell mini 10v almost all the time connected with my external display, but have some issues. One of them is that after every reboot it does not recognize my external display-also after every logout i have ugly screen and the resolution is again not recognized. Also i have conky and cairo-dock running after every reboot although i disabled them in startup (this thread: [http://ubuntuforums.org/showthread.php?t=1402891](http://ubuntuforums.org/showthread.php?t=1402891))

I tried linux mint fluxbox 8 (running on ubuntu 9.19) and there had no such resolution problem with screen resolution)

In the meantime i made this script to activate after reboot
```
#!/bin/sh
xrandr --output LVDS1 --off --output VGA1 --mode 1366x768 --pos 0x0 --rotate normal
conky
cairo-dock -c
```

But hen i have multiple instancies of conky and cairo-dock.

So, is there any way that xubuntu recognize external display, not running unchecked apps...

Where can i, by the way, find start up/session script (maybe manually to delete something)?

---

