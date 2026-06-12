---
title: "wtf?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by avi.thomas on 2006-06-11
hello all...

what are libGLcore and libglx and how do you get them?

ive installed nvidia-glx and nvidia-glx-dev (they dont work)

thanks

---

### Post by fluffington on 2006-06-11
[QUOTE=avi.thomas]hello all...

what are libGLcore and libglx and how do you get them?

ive installed nvidia-glx and nvidia-glx-dev (they dont work)

thanks[/QUOTE]

I'm not sure of the specifics (never bothered to look it up), but they allow you to have a hardware accelerated display. Just installing the packages won't make the drivers work, though. The easiest way to enable the nvidia driver is to open up the terminal and type the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Select nvidia for your driver, disable the dri module (and enable glx if it isn't already) when asked, and configure your monitor/keyboard/mouse according to the directions it gives you.

EDIT: You didn't say what graphics hardware you were using, and I assumed a recent nVidia card. If you're not using nVidia, nvidia-glx is not for you, and if you have an older nVidia card (geForce 2, TNT, etc), then you need the nvidia-glx-legacy package instead.

---

