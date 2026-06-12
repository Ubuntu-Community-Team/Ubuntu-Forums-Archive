---
title: "nVidia drivers"
date: 2022-07-26
forum: Desktop Environments
---

### Post by Autodave on 2022-07-26
Just got Xubuntu 22.04 installed.  However, when I go to Additional Drivers, it tells me that I have a manually installed driver already installed and won't let me pick the 515 driver.  I did not install any driver manually.  How do I fix this?

---

### Post by ActionParsnip on 2022-07-26
What is the output of
```

sudo lshw -C display
dpkg -l | grep -i Nvidia

```
Thanks

---

### Post by Autodave on 2022-07-27
Here is something interesting:  I reinstalled and still have the same thing.  However, when I go into Settings -> nVidia, it shows that I have driver 515 installed which is the newest driver.

---

### Post by #&amp;thj^% on 2022-07-27
Might be fun to look at any "dumps/crash" via:
Dang it, I haven't had my coffee yet>>I fixed the code below
```
xdg-open https://errors.ubuntu.com/user/$(sudo cat /var/lib/whoopsie/whoopsie-id)

```
The page usually starts out reporting no results, but refreshes within 10-30 seconds.
EDIT: You may be looking at this Autodave:
> When Canonical was going to release Ubuntu 22.04 LTS, one of the new things they promised was that Wayland would be activated by default also on computers with NVIDIA graphics cards. Shortly before the final release they backed down, and it is believed that it was because the same hardware company requested it. Later they said they were going to make the driver open source, so it could be included in the kernel, and now they've released NVIDIA 515.48.07, the first open source. 
What shows with:
```
nvidia-smi
```

---

### Post by Autodave on 2022-07-27
Hmmmm.....I pretty much got a blank window.....nothing on it and nothing appearing on it after a minute.  When I tried to close, I got a message saying that a process was still running.

---

### Post by #&amp;thj^% on 2022-07-27
> **Autodave said:**
> Hmmmm.....I pretty much got a blank window.....nothing on it and nothing appearing on it after a minute.  When I tried to close, I got a message saying that a process was still running.

Try again with my fixed code above. BTW it will open in browser.
I'm dangerous in the morning without my coffee...:lolflag:

---

### Post by Autodave on 2022-07-27
dave@dave-MS-7B07:~$ nvidia-smi
Wed Jul 27 14:14:04 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 515.48.07    Driver Version: 515.48.07    CUDA Version: 11.7     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:1F:00.0  On |                  N/A |
| 16%   38C    P8    26W / 175W |    336MiB /  8192MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A      1051      G   /usr/lib/xorg/Xorg                190MiB |
|    0   N/A  N/A      1275      G   xfwm4                               2MiB |
|    0   N/A  N/A      2027      G   ...9/usr/lib/firefox/firefox      140MiB |
+-----------------------------------------------------------------------------+
dave@dave-MS-7B07:~$ 


I sure hope that you understand that stuff!

---

### Post by #&amp;thj^% on 2022-07-27
> **Autodave said:**
> 
I sure hope that you understand that stuff!
:lolflag: 20 years on linux, and I still dont.:)
And you say you never initiated the driver install? is that correct?
I'm still confused with all this information running amuck, IE:
NVIDIA 515.48.07, the first open source version that would open the doors to use Wayland also on computers with these graphics.
source: [https://ubunlog.com/en/nvidia-515-48-07-primera-version-de-codigo-abierto-que-abriria-las-puertas-para-usar-wayland-tambien-en-equipos-con-estas-graficas/](https://ubunlog.com/en/nvidia-515-48-07-primera-version-de-codigo-abierto-que-abriria-las-puertas-para-usar-wayland-tambien-en-equipos-con-estas-graficas/)
And " It seems there is no PPA. I would expect, that soon there should be news that it is added to the kernel. Upgrading can be done with the Ubuntu Mainline Kernel Installer. And if not, by October everything should be implemented."
I'm so far out of touch with Ubuntu now days, I don't have the inside info any longer since I stopped testing Ubuntu.

---

### Post by Autodave on 2022-07-27
I never installed a driver.....I know better! :-)  And that happened on both installations....the first one that I screwed up myself and the second install also.  Weird.  After I had borked the first install by trying to copy something into it to save time, before I borked it I had gone to Additional Drivers to make sure that nVidia was running the latest and greatest.  When I saw that it said a driver had been installed manually, I just ignored that while trying to "save time" and borking the system instead.  After re-installing the second time, I immediately went to Additional Drivers and found the same thing.  Only then did it dawn on me to look for the nVidia icon in Settings.  Finding that and opening it was when I saw that the 515 driver had been installed.  
Also interesting to note here is that under Additional Drivers, there are a bunch of drivers listed from (I believe) 470 through the 515.  However, they are all greyed out and cannot be chosen.

---

### Post by #&amp;thj^% on 2022-07-27
> **Autodave said:**
> I never installed a driver.....I know better! :-)  And that happened on both installations....  However, they are all greyed out and cannot be chosen.
I would expect that on a qualified GPU, as to avoid conflicts between drivers.
So it's happening :o>>>OMG an opensourced Nvidia Driver, I'm curious how this will fare in the long run.
Thanks for the confirmation Autodave..;)

---

### Post by TheFu on 2022-07-27
I'm seeing errors like this with 
```
sudo ubuntu-drivers autoinstall
...
WARNING:root:_pkg_get_support nvidia-driver-515-server: package has invalid Support PBheader, cannot determine support level
...

```
The system has a 1030 GPU (fanless) and Driver Version: 470.129.06.
I'm on the 5.4.x kernels, so that could be my issue.  Not all driver versions are supported by all kernels.

---

### Post by Autodave on 2022-07-28
What will happen when nVidia comes out with a new driver?  Will it auto install, will I be able to upgrade to it, or am I stuck with this one forever?

---

### Post by TheFu on 2022-07-28
> **Autodave said:**
> What will happen when nVidia comes out with a new driver?  Will it auto install, will I be able to upgrade to it, or am I stuck with this one forever?

Nvidia drops support for old hardware periodically.  I only have that GT 1030 because they dropped support for the 7200 GS that was working fine, before I moved to 16.04.  This is why having great F/LOSS drivers is so important for people who use hardware until it actually stops working.  I never plan to buy anything from nvidia again.  Burn me once, .... 

It is only extremely high-end GPUs where nvidia makes sense. They have a leading place there, so if you upgrade the GPU every 1-2 yrs for $1000+, then your should probably keep buying nvidia.  In the mid-performance and below areas, AMD GPUs are easier and have drivers shipped with the kernel.

Something is broken at nvidia. Management there hasn't figured out that people can only use their drivers when they own nvidia hardware already. There's no good reason to withhold source for older GPU drivers. It just pisses people off.

---

### Post by #&amp;thj^% on 2022-07-28
> **Autodave said:**
> What will happen when nVidia comes out with a new driver?  Will it auto install, will I be able to upgrade to it, or am I stuck with this one forever?

Seeing how it is "now in the kernel", it should in theory also be be upgraded, with normal updates and upgrades.
Your the first, here anyway that has shown this New feature

---

### Post by Autodave on 2022-07-28
So I'm the guinea pig.  Yippee.  I guess that I at least did one thing correctly.....I pulled the SSD that 20.04 was on and kept: I can always plug that back in! :-)

---

### Post by #&amp;thj^% on 2022-07-29
> **Autodave said:**
> So I'm the guinea pig.  Yippee.  
Yep you are our Official test user here...:KS
If you can/will keep us updated on this new adventure will ya? ;)
> **Autodave said:**
> I pulled the SSD that 20.04 was on and kept: I can always plug that back in! :-)
A man with a back-up plan...>>> Smart!
> failing to plan is planning to fail

---

### Post by Autodave on 2022-07-29
515.48.07 Is what is currently installed.  I put this here in case I don't remember what one was installed later! :-)  Will keep y'all updated when there is something to update you on!

I will say one thing....the only game I play on Xubuntu is SuperTuxKarts.  With all the graphics turned up the whole way, I am getting 120+ FPS which is higher than I have ever seen on this game.

---

### Post by Autodave on 2022-08-04
Well, it quit today.  Sigh.  When I go into the nVidia icon in Settings, I am presented with no info practically.  I used to have screens of info, now pretty much nothing.  It won't even tell me what driver is being used.  On top of that, my second screen quit functioning...just black.  Going into settings -> Display, it looked normal: second screen on top of main screen.  Nothing changed except that second screen was blank.  I tried making primary screen the secondary, and the secondary the primary.  Then switched them back and applied setting.  Then, I had about 1 1/2" of screen on the primary monitor and 3/4 of a picture on the secondary one.
After spending 10-15 minutes getting back to the Display in Settings (was fun because you could not scroll anything and had to just keep poking on a black screen), I can make the screens mirror, but that is all.  Otherwise I get the top line on the bottom screen and the just part of the background pic on the top screen.
Anyone have an idea?  I am really tired of fighting with 22.04 and am about to try Mint or Kubuntu.

BTW: Win10 works fine with the monitors so I know that cabling is all good.

---

### Post by Autodave on 2022-08-04
Going into Synaptic, it shows that the 515 driver is installed.  Should I maybe try reinstalling?  In Additional Drivers, it still shows that I am using a manually installed driver.  AAARRRGGGHHHH!!!!

Should I uninstall the other driver first?  What is the command for doing that?

---

### Post by ActionParsnip on 2022-08-04
What is the output of
```

sudo lshw -C display
dpkg -l | grep -i Nvidia

```

---

### Post by Autodave on 2022-08-04
$ sudo lshw -C display
[sudo] password for dave: 
  *-display                 
       description: VGA compatible controller
       product: TU106 [GeForce RTX 2070]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:1f:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:71 memory:fc000000-fcffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
  *-graphics
       product: VESA VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=640,480

dpkg -l | grep -i Nvidia
ii  libnvidia-cfg1-515:amd64                   515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-515                       515.65.01-0ubuntu0.22.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-515:amd64                515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-515:i386                 515.65.01-0ubuntu0.22.04.1              i386         NVIDIA libcompute package
ii  libnvidia-decode-515:amd64                 515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-515:i386                  515.65.01-0ubuntu0.22.04.1              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                             amd64        Wayland EGL External Platform library -- shared library
ii  libnvidia-encode-515:amd64                 515.65.01-0ubuntu0.22.04.1              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-515:i386                  515.65.01-0ubuntu0.22.04.1              i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-515:amd64                  515.65.01-0ubuntu0.22.04.1              amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-515:amd64                   515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-515:amd64                     515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-515:i386                      515.65.01-0ubuntu0.22.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  linux-modules-nvidia-515-5.15.0-41-generic 5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41
ii  linux-modules-nvidia-515-5.15.0-43-generic 5.15.0-43.46                            amd64        Linux kernel nvidia modules for version 5.15.0-43
ii  linux-modules-nvidia-515-generic           5.15.0-43.46                            amd64        Extra drivers for nvidia-515 for the generic flavour
ii  linux-objects-nvidia-515-5.15.0-41-generic 5.15.0-41.44+1                          amd64        Linux kernel nvidia modules for version 5.15.0-41 (objects)
ii  linux-objects-nvidia-515-5.15.0-43-generic 5.15.0-43.46                            amd64        Linux kernel nvidia modules for version 5.15.0-43 (objects)
ii  linux-signatures-nvidia-5.15.0-41-generic  5.15.0-41.44+1                          amd64        Linux kernel signatures for nvidia modules for version 5.15.0-41-generic
ii  linux-signatures-nvidia-5.15.0-43-generic  5.15.0-43.46                            amd64        Linux kernel signatures for nvidia modules for version 5.15.0-43-generic
ii  nvidia-compute-utils-515                   515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA compute utilities
ii  nvidia-kernel-common-515                   515.48.07-0ubuntu0.22.04.2              amd64        Shared files used with the kernel module
ii  nvidia-prime                               0.8.17.1                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            510.47.03-0ubuntu1                      amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-515                           515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                    0.18.2                                  all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-515              515.65.01-0ubuntu0.22.04.1              amd64        NVIDIA binary Xorg driver
dave@dave-MS-7B07:~$

---

### Post by #&amp;thj^% on 2022-08-04
Also show:
```
nvidia-smi
```
I'm not sure your driver is broke, maybe something else.
Right now I'm running 2 KVM sessions:
```
Thu Aug  4 11:23:33 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 515.65.01    Driver Version: 515.65.01    CUDA Version: 11.7     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   38C    P8     3W /  N/A |    569MiB /  4096MiB |      3%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A       918      G   /usr/lib/Xorg                     318MiB |
|    0   N/A  N/A      1236      G   /usr/bin/kwin_x11                  38MiB |
|    0   N/A  N/A      1247      G   /usr/bin/plasmashell               85MiB |
|    0   N/A  N/A      4877      G   /usr/lib/firefox/firefox          121MiB |
+-----------------------------------------------------------------------------+


```

---

### Post by Autodave on 2022-08-04
$ nvidia-smi
Failed to initialize NVML: Driver/library version mismatch

---

### Post by #&amp;thj^% on 2022-08-04
Ok what did you do now??? LOL
show:
```
cat /proc/driver/nvidia/version
### It should resemble this:
NVRM version: NVIDIA UNIX x86_64 Kernel Module  515.65.01  Wed Jul 20 14:00:58 UTC 2022
GCC version:  gcc version 12.1.1 20220730 (GCC) 


```
Also this:
```
lsmod | grep nvidia
```
Question, did you receive a kernel upgrade?

---

### Post by Autodave on 2022-08-04
cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  515.48.07  Fri May 27 03:26:43 UTC 2022
GCC version:  


That's what I have.  I even tried going into Synaptic and reinstalling everything for the nVidia driver that had already been installed upon installation.  No difference.

I had a kernel update a couple days ago, but it worked fine after that.

---

### Post by Autodave on 2022-08-04
How do I try and boot into an older kernel (assuming there is one)?  I do not have a grub menu: Xubuntu is installed on a seperate SSD.  Win10 is on its own SSD.

---

### Post by #&amp;thj^% on 2022-08-04
> **Autodave said:**
> cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  515.48.07  Fri May 27 03:26:43 UTC 2022
GCC version:  


That's what I have.  I even tried going into Synaptic and reinstalling everything for the nVidia driver that had already been installed upon installation.  No difference.

I had a kernel update a couple days ago, but it worked fine after that.

So there is no:
```
GCC version:  gcc version 12.1.1 20220730 (GCC)
```
Possible Error.
and i need to see:
```
lsmod | grep nvidia
```

---

### Post by Autodave on 2022-08-04
$ lsmod | grep nvidia
nvidia_uvm           1298432  0
nvidia_drm             69632  1
nvidia_modeset       1142784  1 nvidia_drm
nvidia              40804352  2 nvidia_uvm,nvidia_modeset
drm_kms_helper        307200  1 nvidia_drm
drm                   606208  5 drm_kms_helper,nvidia,nvidia_drm
i2c_nvidia_gpu         16384  0

---

### Post by #&amp;thj^% on 2022-08-04
> **Autodave said:**
> How do I try and boot into an older kernel (assuming there is one)?  I do not have a grub menu: Xubuntu is installed on a seperate SSD.  Win10 is on its own SSD.
EDIT>>>/etc/default/grub
and change to:
```
GRUB_TIMEOUT_STYLE ="menu"
```
to revert back hiding grub use
```
GRUB_TIMEOUT_STYLE ="hidden"
```
and always run this after any change to grub:
```
sudo update-grub
```

---

### Post by Autodave on 2022-08-04
Good grief.....I am thinking that it is time to try something else.  Maybe I will try Ubuntu 22.04 or maybe Mint.  I need to use this machine in 26 hours to host a class in Zoom.  I am thinking that that will have to be done in dreaded Win10 now.

---

### Post by Autodave on 2022-08-04
Typing from my laptop now while Xubuntu 22.04 reinstalls for the third and last time.  It booted up to my install medium and I could manage both monitors right away.  I hope it works this time because I am getting real tired of this.

---

### Post by #&amp;thj^% on 2022-08-04
> **Autodave said:**
> Typing from my laptop now while Xubuntu 22.04 reinstalls for the third and last time.  It booted up to my install medium and I could manage both monitors right away.  I hope it works this time because I am getting real tired of this.

I suspect this will happen again, we haven't addressed or found the problem in the first place.
And you are the first as far as I've yet to see here, that has reported the auto-install of the Nvidia Driver.
I do understand the frustration of not being able to trust your OS when It's crunch time.

---

### Post by Autodave on 2022-08-04
OK....third install done.  However, it will not boot: tells me that

error: file '/boot/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue

Evidently at one time, a grub had been installed on sda.  Just now while reinstalling, it asked me to install grub on sda and it wouldn't....I don't remember the wording of why it wouldn't.  It will not boot into 22.04 by either picking that SSD or by trying the grub on the Win10 SSD.

---

### Post by Autodave on 2022-08-04
OK....after yet another failed install, I d-led Linux Mint.  Install went in about 1/3 the time the Xubuntu took and it is working perfectly.  nVidia was not auto installed, so I installed the 515 driver and it works!  I don't know what is wrong w/Xubuntu, but I hope that they get it fixed someday!

---

### Post by #&amp;thj^% on 2022-08-05
You may have jumped the gun a bit fast, no problems, here.
Autodave I had to see if Nvidia was a automatic install, so my answer is conditional to/for checking the box for "Third Party" will in fact install the Nvidia Driver, IE my install logs: 
```
Start-Date: 2022-08-05  09:18:08
Requested-By: xubuntu (999)
Install: linux-objects-nvidia-515-5.15.0-43-generic:amd64 (5.15.0-43.46+1, automatic), libxnvctrl0:amd64 (510.47.03-0ubuntu1, automatic), libnvidia-common-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libnvidia-fbc1-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), krb5-locales:amd64 (1.19.2-2, automatic), libnvidia-gl-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), gstreamer1.0-plugins-ugly:amd64 (1.20.1-1, automatic), libctf-nobfd0:amd64 (2.38-3ubuntu1, automatic), libnvidia-extra-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), nvidia-compute-utils-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), linux-signatures-nvidia-5.15.0-43-generic:amd64 (5.15.0-43.46+1, automatic), linux-image-5.15.0-43-generic:amd64 (5.15.0-43.46, automatic), chromium-codecs-ffmpeg-extra:amd64 (1:85.0.4183.83-0ubuntu2, automatic), libnvidia-encode-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), nvidia-utils-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libbinutils:amd64 (2.38-3ubuntu1, automatic), libopencore-amrnb0:amd64 (0.1.5-1, automatic), xserver-xorg-video-nvidia-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libopencore-amrwb0:amd64 (0.1.5-1, automatic), binutils-x86-64-linux-gnu:amd64 (2.38-3ubuntu1, automatic), libnvidia-decode-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libnvidia-egl-wayland1:amd64 (1:1.1.9-1.1, automatic), linux-headers-5.15.0-43-generic:amd64 (5.15.0-43.46, automatic), nvidia-kernel-common-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libfile-fcntllock-perl:amd64 (0.22-3build7, automatic), linux-modules-5.15.0-43-generic:amd64 (5.15.0-43.46, automatic), libgstreamer-plugins-bad1.0-0:amd64 (1.20.3-0ubuntu1, automatic), nvidia-prime:amd64 (0.8.17.1, automatic), libctf0:amd64 (2.38-3ubuntu1, automatic), libsidplay1v5:amd64 (1.36.60-1, automatic), screen-resolution-extra:amd64 (0.18.2, automatic), libmpeg2-4:amd64 (0.5.1-9, automatic), nvidia-settings:amd64 (510.47.03-0ubuntu1, automatic), pkg-config:amd64 (0.29.2-1ubuntu3, automatic), linux-modules-nvidia-515-5.15.0-43-generic:amd64 (5.15.0-43.46+1, automatic), binutils-common:amd64 (2.38-3ubuntu1, automatic), libreoffice-help-common:amd64 (1:7.3.5-0ubuntu0.22.04.1, automatic), libdpkg-perl:amd64 (1.21.1ubuntu2.1, automatic), gstreamer1.0-vaapi:amd64 (1.20.1-1ubuntu1, automatic), libva-wayland2:amd64 (2.14.0-1, automatic), linux-modules-extra-5.15.0-43-generic:amd64 (5.15.0-43.46, automatic), libnvidia-cfg1-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), linux-headers-5.15.0-43:amd64 (5.15.0-43.46, automatic), liba52-0.7.4:amd64 (0.7.4-20, automatic), nvidia-kernel-source-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), libnvidia-compute-515:amd64 (515.65.01-0ubuntu0.22.04.1, automatic), gcc-12-base:i386 (12-20220319-1ubuntu1, automatic), libdvdread8:amd64 (6.1.2-1, automatic), binutils:amd64 (2.38-3ubuntu1, automatic), linux-modules-nvidia-515-generic:amd64 (5.15.0-43.46+1)
Upgrade: libext2fs2:amd64 (1.46.5-2ubuntu1, 1.46.5-2ubuntu1.1), linux-headers-generic:amd64 (5.15.0.25.27, 5.15.0.43.44), libtirpc-common:amd64 (1.3.2-2build1, 1.3.2-2ubuntu0.1), libxml2:amd64 (2.9.13+dfsg-1build1, 2.9.13+dfsg-1ubuntu0.1), linux-generic:amd64 (5.15.0.25.27, 5.15.0.43.44), libcom-err2:amd64 (1.46.5-2ubuntu1, 1.46.5-2ubuntu1.1), locales:amd64 (2.35-0ubuntu3, 2.35-0ubuntu3.1), libssl3:amd64 (3.0.2-0ubuntu1, 3.0.2-0ubuntu1.6), mesa-vulkan-drivers:amd64 (22.0.1-1ubuntu2, 22.0.5-0ubuntu0.1), linux-image-generic:amd64 (5.15.0.25.27, 5.15.0.43.44), libtirpc3:amd64 (1.3.2-2build1, 1.3.2-2ubuntu0.1), e2fsprogs:amd64 (1.46.5-2ubuntu1, 1.46.5-2ubuntu1.1)
End-Date: 2022-08-05  09:20:55

```
So if you need any third party software, that gets included.
 My default on install for grub was:
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

```
I've tried to figure out what happened on your end but this is now a mute point.
> I don't know what is wrong w/Xubuntu, but I hope that they get it fixed someday! 
It's even harder for them to fix if you don't file a bug against it. :(
It really dose take a community effort to develop a nicer users experience.. For Now enjoy your Mint install. :)
Your problem could have been as easy as:
```
apt install nvidia-driver-515-server nvidia-utils-515-server
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.15.0-45-generic/updates/dkms/

depmod...
Setting up g++-11 (11.2.0-19ubuntu1) ...
Setting up g++ (4:11.2.0-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up build-essential (12.9ubuntu3) ...

```
That fixed it on my end, I broke it on propose, and enabled the "Proposed" Repo**<<<<(Not Advisable)**
Anyway if you get bored give it shot. :)

---

### Post by Autodave on 2022-08-05
I may throw another SSD in and see what happens.  The grub thing doesn't really bother me because I can just delete it from within Windows.  The graphic thing is the breaker in this deal.  I tried uninstalling, re-installing and nothing worked.  I had to get a working OS with Zoom and 2 screens......and I had 6-8 hours into getting that to happen with Xubuntu and it just wouldn't happen.

I actually thinking about putting an SSD in one of the other machines around here that does not have an nVidia GPU in it.  Then installing 22.04 on that and yank it out of there and hook it into here to see what happens.....if the 515 driver auto installs or if it will allow me to install from the command line or Additional Drivers.  When I get the chance, I will try that and report back.

Thanks to ALL of you for your help!

I'll still be around here....have 9 other machines here running Xubuntu and 2 in other places running it.

---

### Post by #&amp;thj^% on 2022-08-05
For good measure, I placed this: "nvidia-drm.modeset=1" in grub, I'm using this to prevent breakage with kernel upgrades.
So far Its been pretty stable, I changed 3 mainline kernels and going strong.
```
nvidia-smi
Fri Aug  5 15:03:29 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 515.65.01    Driver Version: 515.65.01    CUDA Version: 11.7     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0  On |                  N/A |
| N/A   37C    P8     3W /  N/A |    317MiB /  4096MiB |      6%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A       966      G   /usr/lib/xorg/Xorg                313MiB |
|    0   N/A  N/A      1467      G   xfwm4                               2MiB |
+-----------------------------------------------------------------------------+



```
```
lsmod | grep nvidia
nvidia_uvm           1302528  0
nvidia_drm             69632  3
nvidia_modeset       1146880  5 nvidia_drm
nvidia              40816640  193 nvidia_uvm,nvidia_modeset
drm_kms_helper        311296  1 nvidia_drm
drm                   622592  7 drm_kms_helper,nvidia,nvidia_drm


```
I had a suspicion that a kernel upgrade would break the initial default install Nvidia.
EDIT: Also found the bug you ran into "Nvidia drivers are marked as "auto" at installation and thus removed by `apt autoremove`"
Source: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1955047](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1955047)
Just a re-install works for the right Driver Version.

---

