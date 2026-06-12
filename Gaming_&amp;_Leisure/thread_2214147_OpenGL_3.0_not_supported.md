---
title: "OpenGL 3.0 not supported"
date: 2014-03-30
forum: Gaming &amp; Leisure
---

### Post by ThunderMoon99 on 2014-03-30
[COLOR=#282828][FONT=Verdana]Operating system: Ubuntu 13.10 32bit[/FONT][/COLOR]
[COLOR=#282828][FONT=Verdana]CPU: Intel® Core™ i3 CPU M 370 @ 2.40GHz × 4[/FONT][/COLOR]
[FONT=Verdana][COLOR=#282828]GPU: Intel® Ironlake Mobile x86/MMX/SSE2[/COLOR][/FONT]

[FONT=Verdana][COLOR=#282828]I didn't know whether this should go in here or installation and upgrades because my problems have been with games. I have been playing Minecraft and tried to install the glsl shaders and I kept getting a "[/COLOR][/FONT][COLOR=#282828][FONT=Verdana]Error: Invalid program: gbuffers_terrain" 
[/FONT][/COLOR][COLOR=#282828][FONT=Verdana]>  [Shaders] OpenGL 2.0 = Y    2.1 = Y    3.0 = N    3.2 = N[03:10:20 INFO]: Client> [Shaders] GL_MAX_DRAW_BUFFERS = 8[03:10:20 INFO]: Client> [Shaders] GL_MAX_COLOR_ATTACHMENTS_EXT = 8[03:10:20 INFO]: Client> [Shaders] GL_MAX_TEXTURE_IMAGE_UNITS = 16[03:10:21 INFO]: Client> GL error 0x0502: Invalid operation at useProgram  gbuffers_terrain[03:10:21 INFO]: Client> GL error 0x0501: Invalid value at useProgram  gbuffers_terrain[03:10:21 INFO]: Client> [03:10:21] [Client thread/INFO]: [CHAT] [Shaders] Error : Invalid program gbuffers_terrain[03:10:21 INFO]: Client> [Shaders] Error : Invalid program gbuffers_terrain[03:10:21 INFO]: Client> Program gbuffers_hand loaded[03:10:21 INFO]: Client> Sun path rotation: -40.0f[03:10:21 INFO]: Client> AO Level: 1.0f 
The mod developer said that my driver doesn't support OpenGl 3.0 and to update it, but I did before this with the latest Intel Graphics installer. What do?[/FONT][/COLOR]

---

### Post by dannyboy79 on 2014-03-30
which intel linux driver are you using?

---

### Post by ThunderMoon99 on 2014-03-30
I don't know. How do I check?

---

### Post by dannyboy79 on 2014-03-30
within your /var/log/Xorg.0.log. you may be able to see it using this command
```
cat /var/log/Xorg.0.log | grep Module
```

---

### Post by slooksterpsv on 2014-03-30
IronLake only supports OpenGL 2.1
[http://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units](http://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units)

---

### Post by ThunderMoon99 on 2014-03-31
> **dannyboy79 said:**
> within your /var/log/Xorg.0.log. you may be able to see it using this command
```
cat /var/log/Xorg.0.log | grep Module
```
 This is what I got if you think there might be a way if not all well.
```
 [    23.654] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"[    23.654] (II) Module ABI versions:
[    23.656] (II) LoadModule: "dri2"
[    23.656] (II) Module "dri2" already built-in
[    23.656] (II) LoadModule: "glamoregl"
[    24.277] (II) Module glamoregl: vendor="X.Org Foundation"
[    24.277] (II) LoadModule: "glx"
[    24.277] (II) Module glx: vendor="X.Org Foundation"
[    24.277] (II) LoadModule: "intel"
[    24.323] (II) Module intel: vendor="X.Org Foundation"
[    24.323]     Module class: X.Org Video Driver
[    24.323] (II) LoadModule: "vesa"
[    24.324] (II) Module vesa: vendor="X.Org Foundation"
[    24.324]     Module class: X.Org Video Driver
[    24.324] (II) LoadModule: "modesetting"
[    24.324] (II) Module modesetting: vendor="X.Org Foundation"
[    24.324]     Module class: X.Org Video Driver
[    24.324] (II) LoadModule: "fbdev"
[    24.324] (II) Module fbdev: vendor="X.Org Foundation"
[    24.324]     Module class: X.Org Video Driver
[    24.325] (II) LoadModule: "fbdevhw"
[    24.326] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.328] (II) LoadModule: "dri2"
[    24.328] (II) Module "dri2" already built-in
[    24.328] (II) UnloadModule: "vesa"
[    24.328] (II) UnloadModule: "modesetting"
[    24.328] (II) UnloadModule: "fbdev"
[    24.328] (II) UnloadSubModule: "fbdevhw"
[    24.473] (II) LoadModule: "evdev"
[    24.495] (II) Module evdev: vendor="X.Org Foundation"
[    24.495]     Module class: X.Org XInput Driver
[    24.501] (II) LoadModule: "synaptics"
[    24.501] (II) Module synaptics: vendor="X.Org Foundation"
[    24.501]     Module class: X.Org XInput Driver

```

>  [COLOR=#000000]IronLake only supports OpenGL 2.1[/COLOR]
[http://en.wikipedia.org/wiki/List_of...ocessing_units]("http://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units") 
Thanks for what might have been unsuccessful extra effort. :)

---

