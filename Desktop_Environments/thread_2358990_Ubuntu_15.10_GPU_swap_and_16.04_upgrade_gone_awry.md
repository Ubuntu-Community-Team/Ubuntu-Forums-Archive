---
title: "Ubuntu 15.10 GPU swap and 16.04 upgrade gone awry"
date: 2017-04-19
forum: Desktop Environments
---

### Post by Mr. Universe on 2017-04-19
I've foolishly been using 15.10 still and my Nvidia GTX 680 just kicked  the bucket. I had a GTX 960 on hand but it seemed the Nvidia drivers for  that card weren't available through the graphics drivers PPA for 15.10  so I decided to upgrade. After a long fought process involving mangling  and then removing my sources.list I finally got it to upgrade to  16.04.2. Now it will not start an Xorg environment. I have been trying  everything I can find to get this fixed and I'm at an end. Nothing has  worked so far. The TTYs are locked up most of the time but I have been  able to use SSH to login. Here are some of the things I have tried:
[B]
Start state, Nvidia drivers installed, using lightdm, gdm purged after installing ubuntu-gnome-desktop:[/B]

System freezes on TTY7 and does not respond to anything other than SysRq  commands. There is a log entry on screen from fsck about my SSD that I  am very sure is unrelated.

[B]
Reinstalling the Nvidia drivers:[/B]
```
sudo apt-get purge nvidia*
sudo apt-get install nvidia-375 #Also tried nvidia-current
```

No changes noticeable.

[B]
Update alternatives:[/B]
```
$ sudo update-alternatives --config x86_64-linux-gnu_gl_conf
  Selection    Path                                       Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-304/ld.so.conf              9701      auto mode
  1            /usr/lib/nvidia-304/ld.so.conf              9701      manual mode
* 2            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode

#I then set it to option 1 but it get changed back to 2 after every reboot
```

No changes noticeable.

[B]
Reinstalling desktop components:[/B]
```
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install --reinstall unity
sudo apt-get install --reinstall xorg
``` 

No changes noticeable.

[B]
Remove nvidia:[/B]
```
sudo apt-get purge nvidia*
```

No changes noticeable. I then reinstalled it again.

[B]
Install gdm:[/B]
```
sudo apt-get install gdm
```

Upon restart, it drops to TTY1 and there is screen flicker and the   keyboard misses some presses. After waiting a while it stops flickering  and  can be used as normal. startx does not work.

```
$ startx
```

I get the following output:
[IMG]https://lh3.googleusercontent.com/4pwxw4OswnzLOx3j1w0nzyHke-D0D4e2P_5SJ503JyYZDV-z7YTpSNoOOaGH5iC6ryNwq7OurIOjRB7MDBmFRb2FiK6iXgPUzxswMJyKZkGi26-l5hYqrYGfyzcKNGPEK_06Bu7B4Ts_Zym83R2c3SiGKwo2dDoM5io05BoKyihZnQ1fSgkFXNbGrrFF3j25pcsLsSQtG5LGTeL7LHc6T7IyQHV1k5quUApfinPy2HBRrEP1hepq1IpYL78WRy8NkGRTFTw0HRSKdxwGaClsyi9Oz-iOOvZFDEfXQwcVXzvhmne_Cc3L7opiaAYpwKHsXT55ywpjxKHKnm8Q1e5IPX4WyMDz_c4WarrM8oN6Iq2-geo4qunXu6gcB7prf9f7y_-1r05Bj5JlyPnk2WYUQMEDLCv0VEOCfIBSjst0VGO9KF0lcysRRn4XhdsGMZpvxSGVOVdFhbV6RQm4vN_XshcHOUHU5B-dqid-GI8pDA2cnNM1dmZfCZIFqULWAagMxOdE6JFfi4T-ssZYugEkhm_iuj_XcnKpHfdvOs8KnOeeypvt4IRDCNJDhvvib2TZJWNeWuOZsS4xpqn8EZcWEX-E37g0lvdkDXZ2QbZSm7DcNp5unM-Iop9m0cUxEljcJ5YHg070A0p0ZLmNJvpvfodISIH-Nqyi1Ef6ynB0lw=w1980-h1484-no[/IMG]




The current state is gdm is installed, nvidia-375 is installed, I can  get to the screen in the picture, I cannot get the display manager to  start.
Here is the last [kern.log ]("https://paste.ubuntu.com/24415399/")and [URL="https://paste.ubuntu.com/24415394/"]Xorg.0.log
[/URL]
Here is the output of `ls -R /usr/lib/xorg`
```
/usr/lib/xorg/:
modules  protocol.txt  Xorg  Xorg.wrap

/usr/lib/xorg/modules:
drivers  extensions  input  libexa.so  libfbdevhw.so  libfb.so   libglamoregl.so  libint10.so  libshadowfb.so  libshadow.so  libvbe.so   libvgahw.so  libwfb.so

/usr/lib/xorg/modules/drivers:
amdgpu_drv.so  cirrus_alpine.so  cirrus_laguna.so  intel_drv.so    mga_drv.so          neomagic_drv.so  openchrome_drv.so  r128_drv.so     savage_drv.so         sisusb_drv.so  trident_drv.so  vmware_drv.so
ati_drv.so     cirrus_drv.so     fbdev_drv.so      mach64_drv.so   modesetting_drv.so  nouveau_drv.so   qxl_drv.so         radeon_drv.so   siliconmotion_drv.so  tdfx_drv.so    vesa_drv.so

/usr/lib/xorg/modules/extensions:
libglx.so

/usr/lib/xorg/modules/input:
evdev_drv.so  synaptics_drv.so  vmmouse_drv.so  wacom_drv.so

```

Is there anymore information I can give for diagnosis? What would be the best next step?

---

### Post by Autodave on 2017-04-19
I am hoping someone will have a better anser than I do, but for what its worth......

The GTX 960 should work fine with the newest Nvidia driver. I would install this from the repositories o0nly!

Now, for the big problem. I personally have had almost no luck at all upgrading to a new OS release. Last time I tried, out of about 13 computers, one worked with no probs, 2 kinda worked but had probs that needed rectified, and the rest just plain crashed. I have learned to back up everything and wipe the old install with the new install. Then, recopy the important things back.

---

### Post by Mr. Universe on 2017-04-19
> **Autodave said:**
> I am hoping someone will have a better anser than I do, but for what its worth......

The GTX 960 should work fine with the newest Nvidia driver. I would install this from the repositories o0nly!

I usually only use the repos for the GPU drivers. But I did get a bit desperate on this one and tried to install using the run file from nvidia's site with no luck.

> **Autodave said:**
>  Now, for the big problem. I personally have had almost no luck at all upgrading to a new OS release. Last time I tried, out of about 13 computers, one worked with no probs, 2 kinda worked but had probs that needed rectified, and the rest just plain crashed. I have learned to back up everything and wipe the old install with the new install. Then, recopy the important things back.

That's basically been my experience with upgrades in the past as well. I once got a system to do 3 consecutive upgrades(around 12.04) and it felt like a miracle. I'm just hoping I can some how recover this install. I have a lot PITA vendor software setup that takes good wishes and fair dust to get a successful install. I've never been able to migrate it in the past. For systems that don't have those programs on it I always put a fresh install on when I upgrade.

---

