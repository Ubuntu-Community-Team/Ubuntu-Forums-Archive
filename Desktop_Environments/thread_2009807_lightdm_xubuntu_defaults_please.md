---
title: "lightdm xubuntu defaults please"
date: 2012-06-24
forum: Desktop Environments
---

### Post by gprestonmoto on 2012-06-24
Ok so I tried to change the background picture in lightdm-gtk-greeter.conf and it worked but it's incredibly buggy. So I'm trying to adjust it back to the original settings but do not know the path to the original background, can anyone with xubuntu 64 bit give me the default path?

```
#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=***[COLOR=Black]THIS IS THE PATH I NEED[/COLOR]***
theme-name=Greybird-lightdm
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true

```

---

### Post by rai4shu2 on 2012-06-25
Okay...

```
background=/usr/share/xfce4/backdrops/xubuntu-precise-right.png
```

---

### Post by gprestonmoto on 2012-06-26
> **rai4shu2 said:**
> Okay...

```
background=/usr/share/xfce4/backdrops/xubuntu-precise-right.png
```

Thanks. I know it's kind of stupid but it just looked kind of nuts with a picture. It still ran the xfce loading screen and then switches to a picture real fast, and it doesn't look right. It kind of flashes in and out which it doesn't do using default settings.

---

