---
title: "Gnome and big screens"
date: 2012-03-27
forum: Desktop Environments
---

### Post by luismgl on 2012-03-27
So I have Ubuntu 10.10 installed on my laptop and usually I have it plugged to a 21' screen since that laptop is not that portable anymore and in both upper and lower panels, the icons (trash bin, clock/calendar, etc) that should be on the rightmost side of the screen, are somewhere near the middle, is there a way to change this?

thank you

---

### Post by cortman on 2012-03-27
If your monitor is plugged into HDMI or DVI, simply change the appropriate word-

```
xrandr --output VGA1 --primary 

```

Run in terminal and see if that fixes it. And if you want the laptop monitor to be off-

```
xrandr --output LVDS1 --off
```

---

### Post by luismgl on 2012-03-27
Thanks for the reply, it´s actually plugged via VGA can I use that anyway? Also thanks for the extra info on turning off the laptop display :)

---

### Post by cortman on 2012-03-27
The command is written for VGA, so yes. You can find more info on xrandr (there are a lot of cool display things you can do with xrandr) by running

```
man xrandr
```

---

### Post by luismgl on 2012-03-27
Thanks, got this solved by updating to 11.04, although I don't really like the new unity.

---

### Post by cortman on 2012-03-27
OK, please mark the thread [SOLVED] using the thread tools in the upper right.
Did the xrandr command work?
If you don't like Unity, there's always XFCE, LXDE, KDE, Gnome, etc...

---

### Post by luismgl on 2012-03-27
I actually updated before getting a chance to even see your reply, thanks again for the help though :).

I will give a try other environments, although Unity seems to just need some adaptation time, I might have been too quick to judge.

---

