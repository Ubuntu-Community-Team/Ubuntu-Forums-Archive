---
title: "xrandr mode setting not working"
date: 2009-03-06
forum: Desktop Environments
---

### Post by bazzer on 2009-03-06
I'm trying to get my computer up to 1280x1024, when it boots it goes into 800x600. The resolution setting gizmo does nothing. From a prompt if I do:

```
xrandr --newmode "1280x1024_60" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
xrandr --addmode default 1280x1024_60
xrandr --output default --mode 1280x1024_60 --verbose
```

it just says:

```
screen 0: 1280x1024 339x271 mm  95.85dpi
crtc 0: 1280x1024_60   60.0 +0+0 "default"
xrandr: Configure crtc 0 failed
crtc 0: disable
screen 0: revert
crtc 0: revert
```
and my mode is stuck at 800x600. Think the onboard card is nvidia gefore 6200 based, so the output mode is right - but I've tried VGA, VGA0, VGA1, VGA-0 and nothing works.

---

