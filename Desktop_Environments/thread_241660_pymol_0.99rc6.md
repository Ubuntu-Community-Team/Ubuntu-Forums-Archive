---
title: "pymol 0.99rc6"
date: 2006-08-22
forum: Desktop Environments
---

### Post by veratyr on 2006-08-22
I'm trying to get pymol to work in quad-buffered stereo mode so that it will work in conjunction with a stereo graphics emmiter and glasses for 3d. I'm using an nvidia quadro fx 1400 card with the nvidia-glx drivers from synaptic. Is this possible to do?

---

### Post by veratyr on 2006-08-23
bump.

---

### Post by veratyr on 2006-08-23
Forgot to mention that I am trying to use this with a viewsonic g225f crt which is reported to work in stereo mode. I also came across this info:

[http://pymol.sourceforge.net/stereo3d.html](http://pymol.sourceforge.net/stereo3d.html)

I'm not sure how to try the described modes for the XFree86 config file in an xorg config file.

---

### Post by veratyr on 2006-08-23
Figured it out (sorta). I had to add this option to my device section of my xorg.conf file to get stereo mode to work with the emitter.

```
Option   "Stereo"   "3"
```

Only have one thing left to get working and that is getting the viewsonic g225f to use a refresh rate of 120hz. Iv'e tried using modelines in the monitor section of xorg.conf but nothing seems to work. It's stuck on 85hz. When using windows I had to install a driver from viewsonic to get the refresh rate to work above 85hz. I really hope this isn't the case in linux. I looked on viewsonic's website and couldnt find any type linux driver available.

---

