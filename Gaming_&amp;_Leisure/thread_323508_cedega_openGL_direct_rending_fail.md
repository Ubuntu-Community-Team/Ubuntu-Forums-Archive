---
title: "cedega openGL direct rending fail"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by puntjuh on 2006-12-22
Hi,

I am using ubuntu 6.10 Edgy. And i have succesfully installed cedega ( had some troubles with xlibs but found a dummy package! ). After this i found that i couldn't go further then step 2. It just hung there, this was fixed with dpkg-reconfigure dash. 

Now, i have stepped into a new problem which i cannot seem to fix. The problem is that when i test video, it fails on: "OpenGL Direct Rendering" and it says Passed on: 3D Accelaration!

When doing glxinfo | grep direct i get :

direct rendering: Yes

And doing glxgears -printfps i get:

4993 frames in 5.0 seconds = 998.573 FPS
5013 frames in 5.0 seconds = 1002.593 FPS
4988 frames in 5.0 seconds = 997.531 FPS
5019 frames in 5.0 seconds = 1003.749 FPS

In my xorg.conf is :

Section "Monitor"
    Identifier     "MD7212AZ"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

This is correct for my knowings. 

I just can't seem to figure out why OpenGL Direct Rendering fails. I installed the nvidia drivers using this howto: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) 

I installed it using synaptic, i didn't do it with the latest from nvidia! So my currect version is : 8776. 

Anyone know how I can enable the OpenGL Direct Rendering?

Any help is greatly appreciated!

---

### Post by pay on 2006-12-22
Are you using an amd64 installation?

---

### Post by puntjuh on 2006-12-22
No, i'm using a non 64bit installation.

the kernel is 2.6.17-10-generic!

---

### Post by henrique_guidi on 2006-12-29
I have the same problem with a ATI 9250... Did you get a solution?

---

