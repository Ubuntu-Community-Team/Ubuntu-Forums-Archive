---
title: "xfce's compositor, dri issue ?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ktx on 2006-06-27
Hello, I'm new to this forum :)
I have an ati radeon 9200SE, I managed to make openGL work :D ( following this method : [http://ubuntuforums.org/showthread.php?t=197471](http://ubuntuforums.org/showthread.php?t=197471) )
Problem is : when I enable xfce's compositor in xorg.conf at the next boot xfce looks b0rked (all i can see is the drop-shadows of the windows - see the cap below)
* 3D Acceleration seems to work (all the screensavers show nice fps, compared to previous mesa one) not with compositor on - i can barely see the mouse... ](*,) 

fglrxinfo : 
```

ktx@ktx:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

```

LIBGL_DEBUG=verbose glxinfo
```

ktx@ktx:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
OpenGL extensions:
[i cut the big table and extensions]

```

---

### Post by ktx on 2006-06-27
[[IMG]http://img268.imageshack.us/img268/8095/screenshot60hx.th.png[/IMG]](http://img268.imageshack.us/my.php?image=screenshot60hx.png)
screenshot ^

---

