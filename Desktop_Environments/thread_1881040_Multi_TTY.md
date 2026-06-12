---
title: "Multi TTY"
date: 2011-11-14
forum: Desktop Environments
---

### Post by bluexrider on 2011-11-14
I'm running Oneiric and ATI 9800 all-in-wonder Pro so I have duel display capabilities.

Here the print from  /usr/lib/nux/unity_support_test -p

OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI R350
OpenGL version string:  2.1 Mesa 7.10.2

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

Unity supported:          yes

I can see that it is everything that I need.

Now here is the print from lshw -c video
*-display:0             
       description: VGA compatible controller
       product: Radeon R350 [Radeon 9800 Pro]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:16 memory:d8000000-dfffffff ioport:b800(size=256) memory:ff5f0000-ff5fffff memory:ff5c0000-ff5dffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Radeon R350 [Radeon 9800 Pro] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:d0000000-d7ffffff memory:ff5e0000-ff5effff

I can see I have a UNCLAIMED display.

How can I enable it on say Ctrl+Alt F4

---

### Post by bluexrider on 2011-11-18
Bump

---

### Post by bluexrider on 2011-12-06
bump

---

### Post by bluexrider on 2011-12-15
[http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11](http://maketecheasier.com/run-multiple-x-sessions-without-virtualization/2009/07/11)

---

