---
title: "xgl and beryl stop working"
date: 2007-02-26
forum: Desktop Environments
---

### Post by mitjab on 2007-02-26
i upgrade kernel to 2.6.17-11-386 and all system and then beryl stop working. I reinstall ati drivers to newest one 

```

mitjab@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700
OpenGL version string: 2.0.6334 (8.34.8)

```

and direct_renedering is set to yes

```

mitjab@ubuntu:~$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: MOBILITY RADEON 9700

```

but when i start beryl i get white screen.


I add this to gdm.conf-custom for xgl
```

0=Xgl
[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```


What is wrong?

Thx

---

### Post by mitjab on 2007-02-26
i think the problem is in beryl 0.1.9999. How to get 0.1.4 version?

---

### Post by mitjab on 2007-03-02
anyone?

---

