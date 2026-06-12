---
title: "How can I rotate with xrandr before gdm runs?"
date: 2005-06-03
forum: Desktop Environments
---

### Post by Zed on 2005-06-03
I've got a Dell 1905FP that can rotate to profile orientation, and an Nvidia 5200 that supports rotation. Following the directions [here](http://www.ubuntuforums.org/archive/index.php/t-21111.html) and [here](http://ubuntuforums.org/archive/index.php/t-21185.html), rotation works with a simple ```
xrandr -o left
```But if I leave the monitor in profile, I have to log in and get to a terminal window sideways, and using a trackball sideways is hard. What I'd like to do is just start out rotated from the login screen on. Does anyone know how I'd do that?

Thanks.

---

### Post by Xerampelinae on 2005-06-03
I don't have experience doing this, but I have a suggestion of how it might be done.

You probably have to edit your /etc/X11/xorg.conf file, adding the following line to the video card device section:

Option	"Rotate"	"CCW"

---

### Post by Zed on 2005-06-04
I'm using the "nvidia" driver, not "nv" -- nvidia doesn't support CCW. It's also the case that CCW is exclusive of using xrandr, and I would like to maintain the option of switching back to landscape.

---

