---
title: "Software method to reduce screen brightness"
date: 2010-08-10
forum: Desktop Environments
---

### Post by ingolf,schaefer on 2010-08-10
Hi,

I have a netbook with LED backlight, but even the lowest brightness of the screen is still very bright and eye straining in a dark environment. On Windows and MacOSX there are simple tools that put a borderless more or less transparent black window in front of everything on the screen to reduce brightness even further.

Are there such tools for Ubuntu or other means of achieving the same result?

Thanks for any help.

SOLVED: RedshiftGUI was indeed what I was looking for. Thanks to all for helping me.

---

### Post by stinkeye on 2010-08-10
Try [**_[COLOR="DarkRed"]RedshiftGUI[/COLOR]_**]("http://github.com/maoserr/redshiftgui/downloads")
It's meant to darken your screen at night.
You could probably disable auto-adjust and use it in manual mode.

---

### Post by nick_goodfate on 2010-08-10
you can also add the brightness applet to your panel .

---

### Post by utnubuuser on 2010-08-10
in a terminal:> man xgamma
usage:> xgamma -rgamma .5 -ggamma .5 -bgamma .5

---

### Post by benerivo on 2010-08-10
You can also reduce the gamma, which is different to brightness but may help towards providing the effect you want. In a terminal try...

```
xgamma -gamma 0.8
```

Where 1.0 is standard, and 0.8 is a slight reduction.

EDIT - sorry utnubuuser has already suggested the gamma control option

---

