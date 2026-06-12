---
title: "No dash. No HUD. Unity spitting out errors on an R300 Dell Inspiron 1501."
date: 2012-05-09
forum: Desktop Environments
---

### Post by Ubuntiac on 2012-05-09
I just installed Ubuntu 12.04 on my wifes Dell Inspiron 1501, which uses an R300 ATI graphics chip. Neither the Dash or HUD appear when pushing the appropriate key. When I try unity --reset & in the terminal, I see that over and over it's spitting out:

"r300: CS space validation failed. (not enough memory?) Skipping rendering."

This is just after starting Ubuntu with no apps open, so I find it hard to believe that just rendering the Dash / HUD is completely blowing out the VRAM. Any suggestions on getting this working?

/usr/lib/nux/unity_support_test -p gives:
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS480
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by iMurshaq on 2012-05-09
Complete computer specs?

---

### Post by Ubuntiac on 2012-05-09
Processor: AMD Turion™ 64
ATI R485M, 224Mb shared memory
Graphics bus: PCI-E X16
Memory: 1Gb DDR2

Ubuntu 12.04 64 bit

---

