---
title: "Using other WM than metacity with GNOME?"
date: 2005-11-06
forum: Desktop Environments
---

### Post by commodore on 2005-11-06
Can I do that? And how? I want to use pyWM if that's any help.

---

### Post by 23meg on 2005-11-06
You can. Take a look at Stormy's guide for using Openbox with Gnome for a start:

[http://www.ubuntuforums.org/showthread.php?t=75471](http://www.ubuntuforums.org/showthread.php?t=75471)

---

### Post by commodore on 2005-11-06
How's that supposed to help me? I don't want openbox.

---

### Post by kperkins on 2005-11-06
[QUOTE=commodore]How's that supposed to help me? I don't want openbox.[/QUOTE]
Adapt?

That being said, it looks like pyWM is pretty much beta, and I would imagine has very few users.
From the pywm site:  
> PyWM is in a prototype state, but it's working well enough to offer for download and review.

Be warned that if your scripting has errors, it can take the X server down with it, killing off your apps and causing possible loss of data.
So if you can't figure out how to use it with Gnome, maybe you should stick with metacity, or use openbox, or XCFE, which are all more stable, and don't need so much hacking.
Just my $.02.

---

### Post by commodore on 2005-11-07
I don't really want to use it just try it. It seems very interesting.

I'll install some other distro on my free partition and try it there then so I don't have to risk with my ubuntu.

---

### Post by denkedran on 2005-11-07
you can change the gnome-session windowmanager with the following
open a console and type:
```
gconf-editor /desktop/gnome/applications/window_manager/current
```

but be !! CAREFULL !!
if your gnome-session doesn't start after changing to another windowmanager you could go to a virtual console (STRG+ALT+F1) and revert your changes by typing
```
gconftool-2 --type string /desktop/gnome/applications/window_manager/current "/usr/bin/metacity"
```

good luck

---

### Post by bjourne on 2005-11-07
You can switch WM temporarily. Do this in a shell:

killall -s 9 metacity && fluxbox

In that way, you can just press ctrl+alt+backspace and everything will be back to normal again. Many WMs support the --replace option so you can type:

fluxbox --replace

if you want to try fluxbox for example.

---

