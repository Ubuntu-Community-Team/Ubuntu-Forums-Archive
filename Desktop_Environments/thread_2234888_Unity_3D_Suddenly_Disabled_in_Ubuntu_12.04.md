---
title: "Unity 3D Suddenly Disabled in Ubuntu 12.04"
date: 2014-07-17
forum: Desktop Environments
---

### Post by Malsasa on 2014-07-17
[COLOR=#333333][FONT=UbuntuRegular]My Unity was always OK since first install in 2012. I always use Unity 3D session, never use 2D session. But now, I have only Unity 2D session. I don't want 2D session, I want my 3D session back. I don't know why, now I get **Unity 3D supported:       no** information while I always can use 3D session before.
[/FONT][/COLOR]
[IMG]https://malsasa.files.wordpress.com/2014/07/screenshot-from-2014-07-17-223028.png[/IMG]
[COLOR=#333333][FONT=UbuntuRegular]
Result from /[FONT=courier new]usr/lib/nux/unity_support_test -p[/FONT] command:

[/FONT][/COLOR]
```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

[COLOR=#ff0000]**Unity 3D supported:       no**[/COLOR]
```
[COLOR=#333333][FONT=UbuntuRegular]
Result from [FONT=courier new]dpkg -l | grep xorg-video[/FONT] command:
[/FONT][/COLOR]
```

ii  xserver-xorg-video-ati                 1:6.14.99~git20111219.aacbd629-0ubuntu2  X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus              1:1.3.2-4build1                          X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev               1:0.4.2-4ubuntu2                         X.Org X server -- fbdev display driver
ii  xserver-xorg-video-geode               2.11.13-2build1                          X.Org X server -- Geode GX2/LX display driver
ii  xserver-xorg-video-intel               2:2.17.0-1ubuntu4.4                      X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64              6.9.0-1build2                            X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                 1:1.4.13.dfsg-4build2                    X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic            1:1.2.5-2build2                          X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau             1:0.0.16+git20111201+b5534a1-1build2     X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome          1:0.2.904+svn1050-1                      X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                 0.0.16-2                                 X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128                6.8.1-5build2                            X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon              1:6.14.99~git20111219.aacbd629-0ubuntu2  X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                  1:0.6.3-4build2                          X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage              1:2.3.3-1ubuntu1                         X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion       1:1.7.5-1build2                          X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                 1:0.10.3-3build2                         X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb              1:0.9.4-2build2                          X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx                1:1.4.3-4build2                          X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident             1:1.3.4-2build2                          X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa                1:2.3.0-7build2                          X.Org X server -- VESA display driver
```
[COLOR=#333333][FONT=UbuntuRegular]

Result from [FONT=courier new]lshw -c video[/FONT] command:
[/FONT][/COLOR]
```

  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:dd000000-dd3fffff memory:c0000000-cfffffff ioport:e000(size=64)
```

[SIZE=5]**My Habit**[/SIZE]


[LIST]
[*]I never do upgrade/update packages (but [FONT=courier new]sudo apt-get update[/FONT] is often) and my Unity always be OK until this problem appeared. I don't think not upgrading is a problem source.
[/LIST]

[SIZE=5]**Question**[/SIZE]


[LIST]
[*]What is actually my problem? Why approximately yesterday I can use 3D and now can not?
[*]How to get back my Ubuntu 3D session?
[/LIST]

---

### Post by grahammechanical on 2014-07-17
A couple of points that I have noticed from the information that you have provided.

> OpenGL vendor string: VMware, Inc

Are you running in a virtual machine? Could some setting have changed? Is there enough RAM assigned to the VM? Just guessing here.

> Open GL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)

Gallium 0.4 is the open source video driver for Nvidia cards. It is called Nouveau. Whereas, llvmpipe is a part of Nouveau that is used as a fall back mode when, either the video adapter cannot support Ubuntu Unity 3D or something has happened to stop the proprietary video driver from loading. We also get llvmpipe when we choose Resume from recovery mode.

Try activating another video driver. You will need to reboot afterwards.

this is what I see when I run that unity support test

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.2.3


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

Notice I am running Nouveau but not llvmpipe.

Actually, what you are seeing in not Unity 2D. That has long been discontinued. What you are seeing is an attempt by llvmpipe to give a Unity 3D type experience.

Regards.

---

### Post by kansasnoob on 2014-07-17
> **grahammechanical said:**
> A couple of points that I have noticed from the information that you have provided.



Are you running in a virtual machine? Could some setting have changed? Is there enough RAM assigned to the VM? Just guessing here.



Gallium 0.4 is the open source video driver for Nvidia cards. It is called Nouveau. Whereas, llvmpipe is a part of Nouveau that is used as a fall back mode when, either the video adapter cannot support Ubuntu Unity 3D or something has happened to stop the proprietary video driver from loading. We also get llvmpipe when we choose Resume from recovery mode.

Try activating another video driver. You will need to reboot afterwards.

this is what I see when I run that unity support test


Notice I am running Nouveau but not llvmpipe.

**[COLOR="#FF0000"]Actually, what you are seeing in not Unity 2D. That has long been discontinued.[/COLOR]** What you are seeing is an attempt by llvmpipe to give a Unity 3D type experience.

Regards.

Unity-2D is still supported in Precise and will be throughout April 2017.

---

### Post by kansasnoob on 2014-07-17
I'd guess you had a recent kernel upgrade (possibly also xorg) so post the output of:

```
uname -a
```

---

### Post by kostkon on 2014-07-17
> **grahammechanical said:**
> 
Actually, what you are seeing in not Unity 2D. That has long been discontinued. What you are seeing is an attempt by llvmpipe to give a Unity 3D type experience.
12.04 still has Unity 2d, llvmpipe was added in 12.10, if I remember correctly.

---

### Post by Malsasa on 2014-07-18
Thank you all, for your replies. My [FONT=courier new]uname -a[/FONT] result is

[FONT=courier new]Linux master 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux[/FONT]

---

### Post by Malsasa on 2014-07-18
> **grahammechanical said:**
> 
Are you running in a virtual machine? Could some setting have changed? Is there enough RAM assigned to the VM? Just guessing here.


Thank you. What a comprehensive and total answer. I installed Ubuntu on real machine, my ASUS X44C laptop. My RAM is 2 GB. 

> **grahammechanical said:**
> 
Gallium 0.4 is the open source video driver for Nvidia cards. It is called Nouveau. Whereas, llvmpipe is a part of Nouveau that is used as a fall back mode when, either the video adapter cannot support Ubuntu Unity 3D or something has happened to stop the proprietary video driver from loading. We also get llvmpipe when we choose Resume from recovery mode.

Try activating another video driver. You will need to reboot afterwards.


It seems I started to understand tonight, why my Ubuntu act very strange this last week. Maybe an unknown mechanism leads my Ubuntu to use another driver than usual (the usual is my normal stance of Ubuntu). About your sentence, "*Try activating another video driver*", how to do that? Glad to see your answer here. The clue --*slow but sure*-- comes to me. Thank you.

---

### Post by Malsasa on 2014-07-18
My problem was just solved few seconds ago by changing VGA driver from the wrong NVIDIA Noveau driver llvmpipe into Mesa DRI Intel. I have to show you my bash history until I have solved my problem by following graham clue above. 

**My bash History Tonight**

  ```
398  history | grep xorg
  399  sagr xserver-xorg-video-vmware
  400  sagi xserver-xorg-video-vmware
  401  sudo dpkg-reconfigure xserver-xorg
  402   /usr/lib/nux/unity_support_test -p
  403  dpkg -l | grep xorg-video command:
  404  dpkg -l | grep xorg-video
  405  xserver-xorg-video-fbdev
  406  sudo dpkg-reconfigure xserver-xorg-video-fbdev
  407  sudo vim /etc/X11/xorg.conf
  408  sudo dpkg-reconfigure xserver-xorg
  409  glxinfo
  410  sagi mesa-utils
  411  glxinfo
  412  sudo apt-get purge nvidia*
  413  dpkg -l | grep xorg-video
  414  sudo apt-get purge xserver-xorg-video-nouveau
  415  sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.cadangan
  416  sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64
  417  sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386
  418  sudo vim /etc/X11/xorg.conf
  419  sudo init 6
```

**My Actual Problem**

The Intel driver for my Ubuntu (**Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2**) has accidentally and unknownly changed into **Gallium 0.4 on llvmpipe (LLVM 0x300) **that has no capability to handle my Unity 3D session (and furthermore caused cursor problem I have asked on askubuntu [http://askubuntu.com/questions/498190/cursor-disappearing-after-starting-web-browser](http://askubuntu.com/questions/498190/cursor-disappearing-after-starting-web-browser)). 

Look at these two different driver usage condition from **/usr/lib/nux/unity_support_test -p** command. One when my graphic was broken, one when normal/solved tonight. 

***Broken***

```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

[COLOR=#ff0000]**Unity 3D supported:       no**[/COLOR]
```

***Normal/Solved***

```
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  3.0 Mesa 8.0.2


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


**[COLOR=#ff0000]Unity 3D supported:       yes[/COLOR]**

```
**The Fixation Walkthrough**



[LIST=1]
[*]I searched what graham said above, my Google keyword was: *ubuntu switching driver intel*.
[*]I've landed at askubuntu: [http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work](http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work)
[*]I followed Bruno's solution, the first answer there. Yes I have to edit the solution, though. I have to remove **libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64** from the command. See my bash history above.
[*]I rebooted by sudo init 6, my favorite fastest restart command.
[*]Both of my problems have gone, this problem on this thread and the problem on askubuntu I mentioned above.
[/LIST]

**Conclusion**

I state that my problem was solved. Thank you for all helps and attentions.

---

