---
title: "How to enable mouse/trackball features in Ubuntu 20.04?"
date: 2021-10-01
forum: Desktop Environments
---

### Post by ski-brimson on 2021-10-01
I saw this man page:

[https://www.mankier.com/4/libinput](https://www.mankier.com/4/libinput)

But where is the file I am supposed to configure? I would like to emulate the middle button.  I would like to be able to use my trackball to scroll with a middle button push.  xinput says I am using wayland.  I suspect xinput must be an obsolete command?

I looked under /etc/X11, but the only file ending in .conf is my file xrdp.conf.

This is from sudo libinput list-devices.  The doc says the libinput command cannot be used to change current settings.

```
Device:           Kensington USB OrbitKernel:           /dev/input/event2
Group:            5
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a
```

---

