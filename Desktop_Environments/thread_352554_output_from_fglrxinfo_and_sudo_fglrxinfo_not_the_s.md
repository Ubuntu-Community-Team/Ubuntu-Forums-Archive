---
title: "output from fglrxinfo and sudo fglrxinfo not the same"
date: 2007-02-03
forum: Desktop Environments
---

### Post by DrPrize on 2007-02-03
I've been trying to sort out my graphics card problems - I thought I'd installed the drivers correctly for my ati radeon 9800pro but the output is different depending on whether i'm a root user or not. 

Can someone tell me how I get the user to have the same settings as the root?

Output from fglrxinfo

steve@steve-desktop:~$ fglrxinfo
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

steve@steve-desktop:~$ sudo fglrxinfo
Password:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by DrPrize on 2007-02-03
Fixed it with this info from [http://inferno.slug.org/cgi-bin/wiki?Radeon9000Video](http://inferno.slug.org/cgi-bin/wiki?Radeon9000Video)

Check and modify the permission with...

 % ls -la /dev/dri/
 total 62
 drwxr-xr-x   2 root root     72 2006-02-15 13:27 ./
 drwxr-xr-x  16 root root  62544 2006-02-15 13:23 ../
 crw-rw----   1 root root 226, 0 2006-02-15 13:25 card0

Assign world read,write permissions to card0...

 % chmod 666 /dev/dri/card0
 % ls -la /dev/dri/
 total 62
 drwxr-xr-x   2 root root     72 2006-02-15 13:27 .
 drwxr-xr-x  16 root root  62544 2006-02-15 13:23 ..
 crw-rw-rw-   1 root root 226, 0 2006-02-15 13:25 card0

---

