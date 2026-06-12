---
title: "Tremulous"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by Corey4666 on 2006-07-21
i dont know how to install the tremulous game it has a .run extension and i have no idea what to do #-o

---

### Post by Lord Illidan on 2006-07-21
First, have you got your graphics card drivers installed?

Second, all you have to is load the terminal, navigate to the location of the .run file, and then do this:

```
sh tremulous.run
``` Replace tremulous.run with the true name of the file, of course. You might want to press TAB after the first few letters, so it will autocomplete.

---

### Post by Corey4666 on 2006-07-25
i installed Tremulous and its VERY LAGGY i didnt even get past the menu cuz it lagged every half a second exactly! and the music would skip with the lag and the screen resolution was off ](*,)

---

### Post by jpkotta on 2006-07-25
As Lord Illidan asked, do you have your graphics card set up?  If you run ```
glxinfo | head
``` and it says something about Mesa but not NVidia or ATI or whatever your card is, then your hardware is not set up yet.

---

### Post by Corey4666 on 2006-07-25
:-k 

```
corey4666@corey4666-desktop:~$ glxinfo | head
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_multisample, GLX_NV_float_buffer
client glx vendor string: NVIDIA Corporation

```

---

### Post by jpkotta on 2006-07-26
Hmmm...that looks good.  Maybe your connection is slow?  But I can't imagine that would affect the menu.  Maybe your memory is low?  After just starting, tremulous uses 70MB RAM on my system (225MB total).

Oh yeah, I think it runs a bit better in it's own X server.  CTRL-ALT-F1 to VT1, login, and ```
startx tremulous -- :1
```

---

