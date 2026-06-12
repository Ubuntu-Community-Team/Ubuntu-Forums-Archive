---
title: "Command to turn off display"
date: 2013-03-14
forum: Desktop Environments
---

### Post by Smajjk on 2013-03-14
In xubuntu, are there any way to give a command in the terminal which will turn off the display?

---

### Post by schragge on 2013-03-14
I guess it depends on monitor you're using. You can try ```
sudo apt-get install ddccontrol
``` and play with it.

---

### Post by steeldriver on 2013-03-14
In an X session, you may be able to do it with xrandr - you will need to know the name of the output device e.g. by running 'xrandr -q'

```

$ xrandr -q
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
**LVDS-0 connected** 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1680x1050      60.0*+   50.0  
DVI-D-0 disconnected (normal left inverted right x axis y axis)

```

Then in my case I would turn it off with

```
xrandr --output LVDS-0 --off
```

Setting the value to 'auto' should turn it back on e.g.
```
xrandr --output LVDS-0 --auto
```

---

### Post by stinkeye on 2013-03-14
Try...
```
xset dpms force suspend
```

---

### Post by Smajjk on 2013-03-14
> **stinkeye said:**
> Try...
```
xset dpms force suspend
```

As this seemed like the simplest option I tried it first, and it WORKED! Thank you :)

Btw, I'm on a Thinkpad T61 and this command turned off its display.

---

### Post by jayanth.n.murthy on 2013-11-27
Just run this in the terminal and you are good to go,:)
```
perl -e 'select(undef,undef,undef,.5)' && xset dpms force off
```

---

