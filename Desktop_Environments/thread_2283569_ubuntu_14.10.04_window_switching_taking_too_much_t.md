---
title: "ubuntu 14.10.04 window switching taking too much time"
date: 2015-06-22
forum: Desktop Environments
---

### Post by ltoso on 2015-06-22
Hi, 
i have just install ubuntu on my computer everything else is fine just when i click to open any application it acts in slow motion like, the window starts to appear from faded out to total view take a couple to seconds and then when i open another window, it again does the same, when i tried the ubuntu demo without installing on my system it was working fine, i also stopped animations by using unity tweak tool but it didn't work, 
please recommend

---

### Post by grahammechanical on 2015-06-23
When we use a Ubuntu live session we use an open source video driver. When we install Ubuntu and tick the box "Install third party software" we should get a proprietary video driver.

If there is a reason why the proprietary video driver would not work, or if our graphic adapter does not have the power to run Unity 3D, then we get a fall back open source video driver called llvmpipe. Its purpose is to give an approximation of Unity 3D rendering on graphic adapters that cannot do hardware accelerated 3D rendering. And it is slow.

We also get llvmpipe when we use recovery mode>resume, which is found under the boot menu's Advanced options for Ubuntu label. To see if you are running on llvmpipe go to About this computer in the power/cog menu or open system Settings>Details and see what it says about graphics on that machine. To find out if your graphic adapter can run Unity 3D run this command

```
/usr/lib/nux/unity_support_test -p
```

You should see something like this
> 
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.125

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

Tell us the hardware specification of your machine. Especially, the graphic card and how much of its own memory it has.

Regards.

---

