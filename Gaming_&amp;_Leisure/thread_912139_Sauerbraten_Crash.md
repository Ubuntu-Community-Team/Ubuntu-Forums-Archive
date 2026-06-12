---
title: "Sauerbraten Crash"
date: 2008-09-06
forum: Gaming &amp; Leisure
---

### Post by Zopiac on 2008-09-06
So for quite some time now, when i try to play sauerbraten it says this (when loaded in terminal)

```
Using home directory: /home/Zopiac/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce 6100 nForce 405/PCI/SSE2 (NVIDIA Corporation)
Driver: 1.2 (2.1.2 NVIDIA 169.12)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No texture rectangle support. (no full screen shaders)
Rendering using the OpenGL 1.5 assembly shader path.
init: console
init: gl: effects
init: world
init: sound
init: cfg
Could not set gamma (card/driver doesn't support it?)
sdl: Gamma correction not supported on this visual
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  3777
  Current serial number in output stream:  3779
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f30504ff97c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f30504ffa15]
#2 /usr/lib/libX11.so.6 [0x7f3052a37323]
#3 /usr/lib/libX11.so.6(XESetCloseDisplay+0x3f) [0x7f3052a1ae0f]
#4 /usr/lib/libGL.so.1 [0x7f305464f972]


```

and it crashes when it tries to load the map on startup (right when the music starts playing)

---

### Post by Stargazer989 on 2008-09-06
i'd quote what happened on mine but it froze after i had loaded a multiplayer map... "asteroid" or something.

---

