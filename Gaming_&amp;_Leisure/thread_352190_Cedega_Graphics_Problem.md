---
title: "Cedega Graphics Problem"
date: 2007-02-03
forum: Gaming &amp; Leisure
---

### Post by Bofur on 2007-02-03
Hello, I'm new to Ubuntu and Cedega. I'm at the part after you update and it goes through the tests. My sound passes but it says OpenGL rendering and 3D Acceleration has failed. I was wondering, do I need to get some kinda of driver for my video card(Geforce Go 7900 GS)? I'm on Ubuntu 6.10 and any help would be appreciated. Thanks!

---

### Post by moffa on 2007-02-03
Hello,

In a terminal try typing ```
 glxinfo | grep glx 
```
If it says Nvidia Corporation, you have the proper driver installed for gaming.  If it says Mesa, its not.

I have found the following guide quite helpful:

[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

---

