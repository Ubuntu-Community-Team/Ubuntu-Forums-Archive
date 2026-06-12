---
title: "Steam game crashes on bumblebee [wrong nvidia library loaded]"
date: 2014-08-01
forum: Gaming &amp; Leisure
---

### Post by Mrmazz on 2014-08-01
Hello,

I'm trying to run dota 2 on ubuntu using bumblebee but i can't manage to get it working

I followed the tutorial on this site [http://www.themukt.com/2014/06/13/howto-install-nvidia-331-bumblebee-optimus-cards-ubuntu/](http://www.themukt.com/2014/06/13/howto-install-nvidia-331-bumblebee-optimus-cards-ubuntu/) which seems to have worked

```
maz@mrComputer:~$ optirun glxspheres64 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 555M/PCIe/SSE2
136.269327 frames/sec - 131.901078 Mpixels/sec
134.743671 frames/sec - 130.424328 Mpixels/sec

```

but when i try to run any game using steam i get the following
```
/bin/sh: error while loading shared libraries: libnvidia-tls.so.304.54: cannot open shared object file: No such file or directory
```
even though i got nvidia-331 rather than 304



and also, my unity got broken so i ran 
```
maz@mrComputer:~$ /usr/lib/nux/unity_support_test -p

/usr/lib/nux/unity_support_test: error while loading shared libraries: libnvidia-tls.so.304.54: cannot open shared object file: No such file or directory


```

however, when i run it with optirun, it looks to be functional

```
maz@mrComputer:~$ optirun /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 555M/PCIe/SSE2
OpenGL version string:  4.4.0 NVIDIA 331.89


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



```
what else can i try?

thanks ,
mazz

---

### Post by oldrocker99 on 2014-08-02
You can try the xorg-edgers PPA [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa), which has the nVidia 3.40.24 driver, which may well solve your problem. It solved my X-COM unrecoverable crash in the tutorial.

You might also want to install a lighter-weight desktop for gaming; LXDE (or lubuntu-desktop) or MATE (which uses a few MB less RAM than even LXDE).

---

