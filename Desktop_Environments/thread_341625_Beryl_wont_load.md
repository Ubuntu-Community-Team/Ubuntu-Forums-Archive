---
title: "Beryl wont load"
date: 2007-01-18
forum: Desktop Environments
---

### Post by glockyboots on 2007-01-18
Hi 

I was hoping somebody might know how to help

Ive installed edgy on an inspiron 8200 laptop with a ati radeon 9000 graphics card. After trying out the various drivers i opted for the fglrx propriety driver as it gave by far the best performance. I then proceeded to install xgl/beryl however whenever i log in beryl doesnt work and im reverted to a standard screen slightly clunkier looking than megacity. My gui speed also then gets slow. Im really hoping to get this beryl working and am wondering if anyone has any suggestions?? my fglrx version is 8.28.8

shane@shane-laptop:~$ lsmod | grep fglrx 
fglrx                 406988  8 
agpgart                34888  2 fglrx,intel_agp

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

Regards
Sjame

---

### Post by Pobega on 2007-01-19
Which version of Beryl are you using? If you look at the thread around the top of this page the new beta version if giving everyone problems. If you're using the beta downgrade it to an older version through Synaptic.

---

