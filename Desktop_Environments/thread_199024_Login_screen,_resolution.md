---
title: "Login screen, resolution"
date: 2006-06-18
forum: Desktop Environments
---

### Post by quit on 2006-06-18
Small but annoying problem. When I login to a Gnome session, the resolution is OK but the refresh rate is 65 and needs to be 60 because it upsets my monitor. Anyone know where I set that up?

---

### Post by scxtt on 2006-06-18
check out your /etc/X11/xorg.conf, paying close attn to the "Monitor" section ... you can specify the Horiz and Vert refresh rates ... here's what mine looks like:
```
Section "Monitor"
        Identifier   "Sceptre X20G"
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 65.0
        Option      "DPMS"
EndSection
```

---

