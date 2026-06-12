---
title: "OpenGL Dissappeared - No Launcher, Global Menu Bar"
date: 2014-01-09
forum: Desktop Environments
---

### Post by mikeashelby on 2014-01-09
Hi,

I'm really sorry if this has already been asked, I *have* searched, but to no avail.

Basically, during some updates recently my Ubuntu install has gone awry. The launcher bar doesn't appear, I'm getting no window decoration or global menu bar.

As best I can work out, OpenGL has stopped working (probably because something's gone funny with my restricted drivers - Nvidia GT 610 graphics card, was working fine before, wobbly windows the lot!). However, for the life of me I can't work out how to fix it.

I'm running Ubuntu 13.10. I've reinstalled the nvidia drivers, but that hasn't helped.

Does anyone have any ideas of anything I could try?

Thanks in advance - even if you just point me to where I need to be looking (again, I have googled this over the last 2 days and come up with nothing yet!)

Cheers,

Mike

---

### Post by Frogs Hair on 2014-01-09
With terminal access you can try the following . Try Unity reset first .

Reset Compiz 
```
dconf reset -f /org/compiz/
```
Reset Unity ```
setsid unity
```

---

### Post by mikeashelby on 2014-01-09
You complete winner - that's done it! Been tearing my hair out..

Thank you so much!

---

