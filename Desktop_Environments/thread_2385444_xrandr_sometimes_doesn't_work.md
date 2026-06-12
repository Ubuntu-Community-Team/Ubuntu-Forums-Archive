---
title: "xrandr sometimes doesn't work"
date: 2018-02-20
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-02-20
I think this is because I don't understand how xrandr works. 

A command I use to detect monitor when it's plugged again is done by 
```

xrandr --output DP-1-1-2 --left-of eDP-1-1 --auto --verbose

```
if succeed, output with verbose shows following two lines
```

crtc 0:    1920x1200  59.95 +0+0 "DP-1-1-2"
crtc 1:    1920x1080  59.93 +1920+0 "eDP-1-1"

```



However, executing it the second time after unplug and then plug again, this command seems not taking effect because the external monitor stays black (but other peripherals such as keyboard, mouse, and so on are working without a problem), and the output only display a single monitor.

```

crtc 0:    1920x1200  59.95 +0+0 "DP-1-1-2"

```

Why would the same command have different consequences?

Edit: A solution for auto detecting dual monitor with disper can be checked at [https://ubuntuforums.org/showthread.php?t=2385515](https://ubuntuforums.org/showthread.php?t=2385515)

---

