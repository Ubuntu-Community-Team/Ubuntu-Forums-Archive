---
title: "Adjust screen brightness increment/decrement value"
date: 2024-07-05
forum: Desktop Environments
---

### Post by currentshaft on 2024-07-05
111

---

### Post by him610 on 2024-07-06
You don't say whether you are using X11 or Wayland.
If using X11, you might try some different *xrandr* settings ... 
```
xrandr --output HDMI-A-1 --brightness 0.8 
``` This turns brightness down from nominal 1.0 to 0.8. 
Of course, your *output * entry will be different from mine.
Run just *xrandr* from terminal to determine what display you are using.

---

### Post by currentshaft on 2024-07-06
dn

---

### Post by him610 on 2024-07-06
> No idea. Whatever the default Ubuntu 24 installation came with.

```
echo $XDG_SESSION_TYPE
```

I have one monitor that is really bright so I put the *xrandr* command in a startup file whenever I open a terminal it dims the display.

---

### Post by Holger_Gehrke on 2024-07-07
I don't know Gnome well enough to give you any answers regarding that, but in XFCE / Xubuntu the settings for the number of steps for the brightness keys and whether the steps are linear or exponential is in the power management settings on the first tab ('General').

Holger

---

### Post by currentshaft on 2024-07-07
xs

---

### Post by #&amp;thj^% on 2024-07-07
Yep It works a lot better in a XFCE session.

When I played with Gnome there was a application named "brightness-controller" and it worked better than what Gnome Settings did.

If interested the PPA is here: [https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller/](https://launchpad.net/~apandada1/+archive/ubuntu/brightness-controller/)

---

### Post by currentshaft on 2024-07-08
132 x

---

### Post by vanadium on 2024-07-08
I typically use a command line tool like "light" (you have to find one that works with your GPU) and then bind a script to <Ctrl>XF86MonBrightnessUp/Down that increments/decrements in smaller steps.

---

### Post by #&amp;thj^% on 2024-07-08
+1 with vanadium, and a few more ways.

Well at least you gave it a shot, and much like you feel about XFCE I feel the same as you about Gnome. (Not for Me)

For CLI I'll use:
```
xrandr -q | grep " connected"
eDP-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
HDMI-1-0 connected (normal left inverted right x axis y axis)

```
my cahanges go like:
```
xrandr --output eDP-2 --brightness 0.5
## Or
[code] xrandr --output eDP-2 --brightness 0.8

```
You can add a script to deal with that, 0.5 stands for brightness level and it ranges from 0.0 to 1.0 . 0.0 -> Full black .so you have to choose the required value of brightness .

This doesn't change brightness at a hardware level. 

One more way we have to do this is with another new program named as xbacklight , open your terminal and type this

```
sudo apt install xbacklight
```

then enter this 
```
xbacklight -set 50
```

there 50 stands for brightness range we can get it upto 100 from 0 .

you can also increase and decrease the brightness from present value to specified level.as you mentioned if you want to increase to 10% from current value of brightness then you can give this
```

xbacklight -inc 10
```

and to decrease 10% you can give this
```

xbacklight -dec 10
```

Disclaimer: I haven't used any of the above on Gnome-Shell with Wayland. (For Obvious reasons) 

The first time I installed XFCE on any system, I felt the same as you did, now I won't use anything else. :)

---

### Post by Holger_Gehrke on 2024-07-08
> **currentshaft said:**
> The brightness increment works well with 100 brightness step count. However, XFCE is unusable for me: I can't see anything at 2880x1800 resolution. I open Display settings and change the scale from "1x" to "2x" and everything becomes 4 times smaller instead of larger. What on earth? I thought GNOME was buggy, but this is on another level - not for me.


Yeah, that works inverse to the way it works in most other DEs. It's a multiplier to the resolution, so to get larger visuals you have to use a user-defined multiplier and set it to something smaller than 1 - a value of 0.5 or 0.7 might be good.

Holger

---

### Post by currentshaft on 2024-07-18
dka

---

