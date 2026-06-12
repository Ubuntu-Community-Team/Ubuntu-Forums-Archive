---
title: "ZINK, NVIDIA GTX 1060 6GB , steam"
date: 2023-04-23
forum: Gaming &amp; Leisure
---

### Post by yann20 on 2023-04-23
Hello to all, 
I am under ubuntu 22.04.
I have a nvidia Gtx 1060 6Gb graphics card, drivers 530.41.03.
I would like to use Zink to run my OpenGL games on Steam.
How do I do this please?
Thanks a lot!

---

### Post by #&amp;thj^% on 2023-04-23
I hope your not disappointed, zink is in mesa. it probably depends on the distros packages, but it is probably installed. 
I'm not sure why Nvidia users would want to use Zink, when the proprietary Nvidia driver ships with a good OpenGL implementation. (unless someone is talking about nouveau)
Mike Blumenkrantz replied to a few of us with this recommend for usage:
```

__GLX_VENDOR_LIBRARY_NAME=mesa MESA_LOADER_DRIVER_OVERRIDE=zink GALLIUM_DRIVER=zink
```
Just an example:
```
__GLX_VENDOR_LIBRARY_NAME=mesa MESA_LOADER_DRIVER_OVERRIDE=zink GALLIUM_DRIVER=zink kodi
libva info: VA-API version 1.17.0
libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)

```
EDIT: I'll also add this:
```
MESA_LOADER_DRIVER_OVERRIDE=zink glxinfo | grep OpenGL 
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: NVIDIA GeForce GTX 1650 Ti/PCIe/SSE2
OpenGL core profile version string: 4.6.0 NVIDIA 530.41.03
OpenGL core profile shading language version string: 4.60 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6.0 NVIDIA 530.41.03
OpenGL shading language version string: 4.60 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 530.41.03
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:


```

---

### Post by yann20 on 2023-04-24
Thank you.

---

