---
title: "3d acceleration"
date: 2007-01-11
forum: Gaming &amp; Leisure
---

### Post by jinxy1919 on 2007-01-11
Hi i followed the ati dapper installation guide and it shows the new ati drivers are installed direct rendering is on but only one thing i installed cedega and it run a test and 3d accelertation falied how do i turn that on or what could be the problem any suggestions?

---

### Post by yalex2000 on 2007-01-29
HI!
At me a similar problem :( 

```
ati-driver-installer-8.33.6-x86.x86_64.run
```


```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

```
 $glxinfo | grep -i ren
direct rendering: Yes
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9600 Generic

```

```
$ fgl_glxgears 
Using GLX_SGIX_pbuffer
2091 frames in 5.0 seconds = 418.200 FPS
2790 frames in 5.0 seconds = 558.000 FPS
2854 frames in 5.0 seconds = 570.800 FPS
2815 frames in 5.0 seconds = 563.000 FPS
2801 frames in 5.0 seconds = 560.200 FPS

```

```

$ glxgears -printfps
1157 frames in 5.0 seconds = 231.364 FPS
966 frames in 5.0 seconds = 193.036 FPS
1053 frames in 5.0 seconds = 210.596 FPS
605 frames in 5.0 seconds = 120.995 FPS
985 frames in 5.0 seconds = 196.991 FPS
1175 frames in 5.0 seconds = 234.989 FPS
1147 frames in 5.0 seconds = 229.385 FPS
1139 frames in 5.0 seconds = 227.796 FPS
1160 frames in 5.0 seconds = 231.990 FPS

```

Help!!!

---

