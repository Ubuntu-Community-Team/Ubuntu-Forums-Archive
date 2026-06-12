---
title: "sdlmame, ati 4870, catalyst 8.9, opengl mode = back to desktop"
date: 2008-09-29
forum: Gaming &amp; Leisure
---

### Post by talz13 on 2008-09-29
I just got sound working in sdlmame so I'm starting to get excited about the possibilities of mame'ing on here, but I'm still limited to using 'soft' mode in mame to actually run games.  If I switch back to 'opengl' mode, the mame screen disappears and I'm left staring at my desktop (despite sdlmame still running in the terminal, and still showing up in 'ps aux | grep sdlmame').

It doesn't get to the "move the joystick left and right to continue" screen, nothing.  It just up and half-quits.  If I go back into my /etc/sdlmame/mame.ini and change from:```
#
# VIDEO OPTIONS
#
video                     opengl
#video                     soft
numscreens                1
window                    0
keepaspect                1
unevenstretch             1
effect                    none
centerh                   1
centerv                   1
waitvsync                 0
``` to:```
#
# VIDEO OPTIONS
#
#video                     opengl
video                     soft
numscreens                1
window                    0
keepaspect                1
unevenstretch             1
effect                    none
centerh                   1
centerv                   1
waitvsync                 0
``` it starts working again, albeit more slowly than normal, and has odd refresh lines going across the screen on some games (sf3 3rd strike in particular, the capcom logo is a great example of this).

```
jeff@server:~$ glxinfo | grep direct
direct rendering: Yes
jeff@server:~$ 
```
```
jeff@server:~$ glxinfo | grep ATI
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_shader_texture_lod, GL_ATI_texture_compression_3dc, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, GL_EXT_abgr, 
jeff@server:~$ 
```

After I remembered to turn of vsync, I got:
```
jeff@server:~$ glxgears
28705 frames in 5.0 seconds = 5736.751 FPS
26956 frames in 5.0 seconds = 5391.131 FPS
31535 frames in 5.0 seconds = 6306.859 FPS
32551 frames in 5.0 seconds = 6510.150 FPS
32209 frames in 5.0 seconds = 6441.744 FPS

jeff@server:~$ 
```

I am using the latest catalyst 8.9 drivers from the ati site.  Should I remove those and try different drivers?

---

### Post by FranMichaels on 2008-09-29
Does changing this option from 1 to 0 help?
# OpenGL-SPECIFIC OPTIONS
#
filter                    0

That solved my slow opengl mode problem.

If the opengl mode doesn't work period, the ati drivers are to blame. Do the open source drivers provide acceleration on your card?

---

### Post by talz13 on 2008-09-30
Yeah, opengl doesn't work at all in mame.  It just cuts out to the desktop, no mame picture at all after the game select screen.

I tried HL2 this morning and was greeted with crazy extended scene filling polygons whenever a character was on the screen, gonna try a couple other things when I get home, then I might try installing the open source driver.

---

