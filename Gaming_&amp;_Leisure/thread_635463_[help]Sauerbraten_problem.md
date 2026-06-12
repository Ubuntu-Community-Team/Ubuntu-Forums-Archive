---
title: "[help]Sauerbraten problem"
date: 2007-12-08
forum: Gaming &amp; Leisure
---

### Post by k0rfain on 2007-12-08
Ok well, i just reinstalled ubuntu gutsy. (left debian again), and now sauerbraten isnt working to well. when I play it it runs very very slow.
And this is what I get;

```
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: Mesa GLX Indirect (Mesa project: www.mesa3d.org)
Driver: 1.4 (2.1 Mesa 7.0.1)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
WARNING: No shader support! Using fixed function fallback. (no fancy visuals for you)
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No framebuffer object support. (reflective water may be slow)
WARNING: Non-power-of-two textures not supported!
init: console
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.4 seconds)
Mining Station by metlslime
game mode is ffa/default

```

---

### Post by rahimveron on 2007-12-09
Turning off shades and other effects solved my problem

---

### Post by dfreer on 2007-12-09
> Renderer: Mesa GLX Indirect (Mesa project: [www.mesa3d.org](www.mesa3d.org))
I'm guessing, your video card isn't set up correctly. Although I'm not at all a sauerbraten expert.

---

