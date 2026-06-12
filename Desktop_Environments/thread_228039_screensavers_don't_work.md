---
title: "screensavers don't work"
date: 2006-08-02
forum: Desktop Environments
---

### Post by louis_nichols on 2006-08-02
Hi folks!

Here's the thing: most of my screensavers don't work. For example Flux, GLMatrix, GFlux, GLBlur and others. I think they are the GL ones. Others work fine (Galaxy, Fuzzy Flakes etc.)

I have no idea why this is. It probably has something to do with my playing around in order to get compiz to work, but I don't know what I have to un/re-do.

I need some pointers...

EDIT: I have to mention that everything else works ok, graphicswise...

---

### Post by 23meg on 2006-08-03
Just to rule this out, are you sure that the packages xscreensaver-gl and xscreensaver-gl-data are installed?

---

### Post by wylfing on 2006-08-03
You might also try running the following command in a terminal:
```
glxgears
```
You should get a nice picture of 3 gears on your screen. If you get errors (e.g., a segmentation fault), then you've got issues with your video card and perhaps we can help you diagnose that.

---

### Post by louis_nichols on 2006-08-04
thanks a lot for the replies, guys.

yes, I have everything installed.

when I run glxgears, I get

```
myself@home:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

I checked my xorg.conf file and it looks ok to me, though...

---

### Post by louis_nichols on 2006-08-04
strike the last!

I didn't know what to do, so I decided to try tseliot's script to install the latest nvidia drivers, and it worked.

I never could get the 8762 driver to work, anyway, (some bug about the api missmatch) so now I shot 2 rabbits with one bullet...

thanks for your help!

---

