---
title: "Fullscreen steam games not working properly"
date: 2014-08-20
forum: Gaming &amp; Leisure
---

### Post by scherdee on 2014-08-20
If I run Portal or Dota 2 on Ubuntu 14.04 I can hear sounds but can't see picture and can't focus it's window. May it be caused by last steam update (today, 3.1mb)?
Some info about PC: 
```
OpenGL vendor string: NVIDIA CorporationOpenGL renderer string: GeForce GT 635M/PCIe/SSE2
OpenGL core profile version string: 4.3.0 NVIDIA 331.38
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.4.0 NVIDIA 331.38
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:

```

---

### Post by oldrocker99 on 2014-08-20
It could also be the nVidia driver. I'm using 3.43.13, which I got from the xorg-edgers PPA.
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-343
```

This **may** solve your problem, and it will do no harm.

---

