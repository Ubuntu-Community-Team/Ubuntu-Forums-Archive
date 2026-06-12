---
title: "Monitor dev name is different from that in xrandr"
date: 2018-02-20
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-02-20
I am trying to auto execute a script when the monitor is re-plugged. 

And I notice that the dev names found in /sys/class are different from that with xrandr.

Output under /sys/class/drm/card1
```

/sys/class/drm/card1/card1-DP-1/
/sys/class/drm/card1/card1-DP-2/
/sys/class/drm/card1/card1-DP-3/
/sys/class/drm/card1/card1-DP-5/
/sys/class/drm/card1/card1-DP-6/
/sys/class/drm/card1/card1-eDP-1/
/sys/class/drm/card1/card1-HDMI-A-1/
/sys/class/drm/card1/card1-HDMI-A-2/

```

Output by randr 
```

eDP-1-1
DP-1-1
HDMI-1-1
DP-1-2
HDMI-1-2
DP-1-1-1
DP-1-1-2
DP-1-1-3

```

Testing to see if I can apply xrandr using output found in /sys/class with 

```

xrandr --output DP-5 --left-of eDP-1 --auto

```


It fails because xrandr complains 

```

warning: output DP-5 not found; ignoring

```

Manually run xrandr, picking up display dev name, and applying with xrandr works without a problem like below
```

xrandr --output DP-1-1-2 --left-of eDP-1-1 --auto

```

but I need to automate the process. So my question is how can I pick the correct name when auto executing xrandr (more specifically, find the name in /sys/class/ and match that name to xrandr)? Any way to achieve such effect?

Thanks

---

