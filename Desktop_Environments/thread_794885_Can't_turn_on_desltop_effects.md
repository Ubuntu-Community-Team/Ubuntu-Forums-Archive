---
title: "Can't turn on desltop effects?"
date: 2008-05-15
forum: Desktop Environments
---

### Post by mark_lar on 2008-05-15
Hi,

I had the desktop effects running nicely on Ubuntu 7.10. However, since I updated to 8.04, I can't turn them on. Any idea if this is just a new bug?

Mark

---

### Post by Living2007 on 2008-05-15
Is your video card supported by the new OS?

---

### Post by Canis familiaris on 2008-05-15
Which graphics card are you using?
Post the output of the following commands:
```
glxinfo | grep direct
lshw -C video

```
(EDIT: there was a typo, not glxingo but glxinfo)

---

### Post by mark_lar on 2008-05-15
It's a ATi Mobility Radeon 7500. It's strange that the effects work in 7.10 but not 8.04. If I go to System --> Preferences --> Appearance --> Visual effects then select any, It starts to load and then says "Couldn't start visual effects".

---

### Post by mick222 on 2008-05-15
same problem
glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
how do i set libgl_direct to verbose

---

### Post by Living2007 on 2008-05-15
I have a similar problem with my card on 7.10, because my card (nVidia GForce MX 4000) came out in 2005, and Ubuntu 7.10 in 2007, the card won't work because it doesn't have good specs. for visual effects to work, unless i download the file "nvidia - glx"

You may have to do a similar thing, just find out what file needs to the downloaded

---

### Post by Canis familiaris on 2008-05-16
> **mick222 said:**
> same problem
glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
how do i set libgl_direct to verbose

Install your graphics card drivers. If you use nVidia or ATi try Envy.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

