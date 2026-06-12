---
title: "Problems with videocard in Dell Latitude C640..."
date: 2007-02-20
forum: Desktop Environments
---

### Post by jmorrissey3 on 2007-02-20
I have loaded Ubuntu 6.10 on my Dell Latitude C640.  The system has 1gb of memory, a 20gb hard disk, and Ubuntu loaded fine (network, sound, display).  When typing glxingo | grep Mesa, I get the following output:

john@agent-smith:~$ glxinfo | grep Mesa
libGL warning: 3D driver claims to not support visual 0x4b
OpenGL renderer string: Mesa DRI Radeon 20060327 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1

What do I have to do to correct this?  I want to be able to run my windows games in Ubuntu, either with Wine or Cedega, and the libGL warning: 3D drivers claims to not support ..... is stopping me.

Let me know if you need any more info.  Any help is greatly appreciated!

**I am able to run glxgears (it opens up the window with the gears turning), but no FPS info (or anything else except libGL warning: 3D driver claims to not support visual 0x4b) appears.**

John

---

