---
title: "Compiz 3D Windows"
date: 2013-06-06
forum: Desktop Environments
---

### Post by LinuxWillWin on 2013-06-06
Hi Ubuntu fans,

In compiz I enabled "cube" and "rotate cube". If I enable "3D Windows" in Compiz and rotate the cube it looks like in the picture in the attachments.
Did anyone of you had this issue before? I use the Onboard graphics "AMD Radeon HD 3000" on my Gigabyte GA-78lmt-USB3 Motherboard. My processor is the AMD FX6300. 
The command "[COLOR=#000000]/usr/lib/nux/unity_support_test -p" shows me the following:
[/COLOR]> OpenGL vendor string:   X.OrgOpenGL renderer string: Gallium 0.4 on AMD RS780
OpenGL version string:  3.0 Mesa 9.1.3


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


Unity 3D supported:       yes[COLOR=#000000]
Hope someone can help me[/COLOR]:D

---

### Post by dino99 on 2013-06-06
are you sure that hd3000 is 3D compatible ? (i have some doubts)

---

### Post by LinuxWillWin on 2013-06-06
I think so. Cairo Dock and the cube without the 3D windows works.

---

### Post by deadflowr on 2013-06-06
3d windows has been broken for a good while.
At least since quantal came out.
If the cube looks good without it, then just don't enable it.
Here's a bug on the issue

[https://bugs.launchpad.net/compiz/+bug/1024208](https://bugs.launchpad.net/compiz/+bug/1024208)

---

### Post by LinuxWillWin on 2013-06-07
Thank you! :)

---

