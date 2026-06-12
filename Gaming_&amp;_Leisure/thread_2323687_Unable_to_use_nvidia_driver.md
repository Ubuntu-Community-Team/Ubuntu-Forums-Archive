---
title: "Unable to use nvidia driver"
date: 2016-05-07
forum: Gaming &amp; Leisure
---

### Post by tubelius2 on 2016-05-07
I've had major trouble trying to get Nvidia driver to work on my HP OMEN 15-5250no 15,6". It has GeForce GTX 960M + Intel GPU. I'm running Ubuntu 14.04.4 LTS 64bit. Installed it like a month ago when I bought this PC. Xorg driver works, but Minecraft isn't running well with it (low FPS, some chunks fail to render, crashes). I've tried at least 5 different versions of nvidia driver, including 361 and 364. 

I always get one of these issues:
[LIST]
[*]black/blank screen when I hear the login sound (sometimes starts to work if I wait over 10min) 
[*]login loop (with all users, but only when using nvidia driver) 
[*]it just uses intel GPU. 
[/LIST]

I've tried different kernels: 

[LIST]
[*]linux-image-4.2.0-35-generic: After I hear the login sound, I have to wait over 10min until I get a login screen. Then it will work fine and actually use the Nvidia driver. With nvidia-361 I get nice performance with Minecraft even. But I don't really want to wait for 10-30min every time I login. 
[*]linux-image-4.5.3-040503-generic: Renames my xorg.conf into xorg.conf.<date> and resets prime setting from nvidia to intel. So I cannot use the Nvidia driver to get some performance on Minecraft. 
[*]linux-image-4.6.0-040600rc2-generic: Login loop with nvidia driver. 
[/LIST]

Things tried:
> sudo apt-get purge nvidia*
sudo apt-get install nvidia-352 nvidia-prime
cp /etc/X11/xorg.conf.05072016 /usr/share/X11/xorg.conf.d/xorg.conf

rubiksmomo@acidburn:/etc/X11$ sudo prime-select nvidia
Error: alternatives are not set up properly
Error: nvidia mode can't be enabled
rubiksmomo@acidburn:/etc/X11$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf
There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-352/ld.so.conf              8604      auto mode
  1            /usr/lib/nvidia-352-prime/ld.so.conf        8603      manual mode
  2            /usr/lib/nvidia-352/ld.so.conf              8604      manual mode
* 3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

Press enter to keep the current choice
[*], or type selection number: 0
update-alternatives: using /usr/lib/nvidia-352/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
rubiksmomo@acidburn:/etc/X11$ sudo prime-select nvidia

sudo reboot

(Booted 4.5.3 kernel and logged in. Got 864x486 resolution and no other resolutions are available. From Nvidia settings I could see that it has changed back to Intel. After renaming /usr/share/X11/xorg.conf.d/xorg.conf I got the resolution fixed, but I still cannot select nvidia from prime settings.)


Me and the users on #ubuntu @ Freenode IRC channel are running out of ideas. What else could I try?

---

### Post by MikeCyber on 2016-05-07
I usually install the first time the nvidia from the repos with synaptic and later update with downloads from nvidia.
Never had any problems, so maybe try from scratch again as you could easily have messed up someting.

---

### Post by tubelius2 on 2016-05-07
> **MikeCyber said:**
> I usually install the first time the nvidia from the repos with synaptic and later update with downloads from nvidia. Never had any problems, so maybe try from scratch again as you could easily have messed up someting.  I downloaded: [http://us.download.nvidia.com/XFree86/Linux-x86_64/361.42/NVIDIA-Linux-x86_64-361.42.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/361.42/NVIDIA-Linux-x86_64-361.42.run) (and made it executable)  I ran: ```
sudo apt-get purge nvidia* sudo stop lightdm sudo ./NVIDIA-Linux-x86_64-361.42.run
```  Tried to install, but the installer cannot find my kernel headers: [https://paste.ubuntu.com/16279514/](https://paste.ubuntu.com/16279514/). After this I had login loop so I installed: nvidia-361 nvidia-prime. I can login again, but it refuses to use nvidia.  Some additional details: [https://paste.ubuntu.com/16279565/](https://paste.ubuntu.com/16279565/) . dpkg -l linux-headers* | nc termbin.com 9999 [http://termbin.com/fngf](http://termbin.com/fngf).

---

### Post by tubelius2 on 2016-05-07
There's something wrong with the headers for the kernels I installed manually. I managed to install the nvidia driver manually on linux-image-4.2.0-35-generic. I had the same issue, it just uses Intel driver. If I try to select nvidia on prime settings using GUI it throws me a blank error dialog. If I use "sudo prime-select nvidia", it will complain about "alternatives not properly set".

---

### Post by MikeCyber on 2016-05-08
That's why I first install the nvidia driver from synaptic as it installs headers etc.. I also have a integrated Intel graphics but never bothered to install that so far. I will wait until it works out of the box, probably Vulkan 
will be able to use both simultaneously in the near future.

---

