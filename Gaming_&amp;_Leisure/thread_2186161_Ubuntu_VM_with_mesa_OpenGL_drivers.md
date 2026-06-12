---
title: "Ubuntu VM with mesa OpenGL drivers"
date: 2013-11-06
forum: Gaming &amp; Leisure
---

### Post by roxxxance on 2013-11-06
Hello all.

I'm struggling with mesa drivers on ubuntu VM (already tried 12.04 and 13.10) using VMWARE.

Some games like Half-Life works, but others don't.

As I'm trying to run some OpenGL 3 games on steam, I get the following error:

Could not find required OpenGL entry point 'glColorMaskIndexedEXT'! Either your video card is unsupported, or your OpenGL driver needs to be updated.

A also tried using [COLOR=#000000][FONT=Tahoma]*export MESA_EXTENSION_OVERRIDE=GL_EXT_draw_buffers2 *[/FONT][/COLOR] so the error can be ignored, but as I expected, the game does nothing but launch a blackscreen (with game sounds!).

I tried llvmpipe, and this seems to work but it is incredibly slow as everything is done by CPUs.

Does anybody knows how to solve this issue ?

More infos:

root@ubuntu:~# dpkg -l|grep libgl1-mesa-dri
ii  libgl1-mesa-dri:amd64                     9.2.1-1ubuntu3                          amd64        free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-dri:i386                      9.2.1-1ubuntu3                          i386         free implementation of the OpenGL API -- DRI modules




root@ubuntu:~# glxinfo|grep OpenGL
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on SVGA3D; build: RELEASE;  
OpenGL version string: 2.1 Mesa 9.2.1
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by DanglingPointer on 2013-11-06
In my humble opinion, you shouldn't be playing AAA or OpenGL-heavy games on a vm.  That would be your first and foremost issue.
Second, if you have a look at the tests done at Phoronix, the propriety drivers are the best by a good margin.
Third, trying to satisfy the second point above, then trying to get propriety drivers working on a vm could prove very difficult as there is an extra abstraction layer between linux, the host OS and the hardware.  Mesa drivers on OpenGL-heavy apps have issues without a VM, imagine running in one it would be even worse!

In summary you are better off dual booting or making a decision on whether to swallow the blue pill (M$ Windows) or the red pill (Linux).

---

