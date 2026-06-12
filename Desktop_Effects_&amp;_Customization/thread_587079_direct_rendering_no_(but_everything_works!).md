---
title: "direct rendering: no (but everything works?!)"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by tisto on 2007-10-22
Just installed a fresh copy of gutsy (7.10) on my IBM Thinkpad T60 laptop (ATI X1400).

Now i got 3d desktop running (compiz) with the cube and other eye candy stuff, no problems. 

I run glxgears i get:
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
58848 frames in 5.0 seconds = 11738.212 FPS
36827 frames in 5.0 seconds = 7349.540 FPS
36227 frames in 5.0 seconds = 7223.922 FPS
35888 frames in 5.0 seconds = 7159.191 FPS
36468 frames in 5.0 seconds = 7284.855 FPS

```

I have no idea if those numbers are any good??

I run glxinfo and get:
```
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400

```

What i can see is that i have no direct rendering, so am i all newbie style no clue, but am thinking no dri no compiz or have i lost it all?

How can i have no dri but can have compiz running without any problems? is not dri the 3d acc driver for xfree?

Can anyone be kind to explain to me? :confused:

//Tisto

---

### Post by nahham on 2007-10-23
I have the same problem and was wondering what is wrong.  Everything works except for videos encoded in Divx5 which display a green line and bad colors when playing (see attachment). By the way I have a Thinkpad T60p.

Any ideas??

---

### Post by terdon on 2007-11-11
Yeah, I get the same thing... Still trying to figure it out. I saw in some thread around here (sorry, lost the link) that the direct rendering: no thing is some issue of communication between fglrx and glX (?)

What I understood is that basically getting the > 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".


message does not mean there is no direct rendering but just that glx thinks there isn't.

In any case, the video thing you mentioned is not a problem if you use mplayer.

---

### Post by jimerickso on 2007-11-11
if you are using vlc you could try selecting xshm as the video driver. that might help.

---

### Post by Rob Campbell on 2007-11-12
Yes, I managed to get around the problem of the green bar by using VLC and fiddling with the video output options. Still thinks it has no direct rendering, however, and so I can't play Quake 4. :-/

---

