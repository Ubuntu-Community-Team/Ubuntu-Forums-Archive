---
title: "TORCS crashes when racing on some tracks."
date: 2010-09-10
forum: Gaming &amp; Leisure
---

### Post by mahela007 on 2010-09-10
I ran TORCS in terminal. 
THe following is the output when the game crash```
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
OpenAL backend info:
  Vendor: OpenAL Community
  Renderer: OpenAL Soft
  Version: 1.1 ALSOFT 1.12.854
  Available sources: 256
  Available buffers: 1024 or more
  Dynamic Sources: requested: 235, created: 235
  #static sources: 21
  #dyn sources   : 235
*********************************WARN_ONCE*********************************
File radeon_swtcl.c function r100_swtcl_flush line 323
Rendering was 1 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
refresh: ssgCullAndDraw invalid enumerant
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 256 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 22 Buffer(s)

```

---

### Post by mahela007 on 2010-09-10
uumm... Here's what happened when the track loaded properly but failed after a few seconds of playing.
```
Compatibility mode, properties unknown.
WARNING: ssgLoadTexture: Cannot determine file type for './(null)'
OpenAL backend info:
  Vendor: OpenAL Community
  Renderer: OpenAL Soft
  Version: 1.1 ALSOFT 1.12.854
  Available sources: 256
  Available buffers: 1024 or more
  Dynamic Sources: requested: 235, created: 235
  #static sources: 21
  #dyn sources   : 235
*********************************WARN_ONCE*********************************
File radeon_swtcl.c function r100_swtcl_flush line 323
Rendering was 1 commands larger than predicted size. We might overflow  command buffer.
***************************************************************************
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
refresh: ssgCullAndDraw invalid enumerant
drmRadeonCmdBuffer: -22. Kernel failed to parse or rejected command stream. See dmesg for more info.
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)
AL lib: ALc.c:1420: alcDestroyContext(): deleting 256 Source(s)
AL lib: ALc.c:1818: alcCloseDevice(): deleting 25 Buffer(s)

```

---

