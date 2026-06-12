---
title: "Dell XPS 15z + Ubuntu Gnome 13.10 - Noisy, Hot, Low Batt. life EVEN w/ TLP"
date: 2013-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adamzendarski on 2013-12-16
Hi,

[SIZE=3]I have a Dell XPS 15z (L511z) with Ubuntu Gnome 13.10 and I have always had a problem (even after installing TLP and doing other things) with a very hot surface, a noisy maxed RPM fan, and a low battery life.

I have really had a problem since version 12.04. *The only thing that has ever truely helped since 12.04 was Laptop Mode Tools.* TLP hasn't helped nearly as much as Laptop Mode Tools did when it was active.

**I have ***already*** done the following:** Installed TLP, installed the proper graphics drivers, added boot parameters, cleaned all of the internal hardware, added Arctic Silver 5 to the CPU and around the GPU, removed some black hard plastic latice piece covering the bottom air intake and speakers (which actually helped a lot), *installed an SSD*, and many other things.

Basicly what I am wondering is if anyone else was able to find a fix, hack, config mod, or whatever it may be that worked for you to resolve problems I am experiencing.

[SIZE=3]Can anyone please offer any suggestions to what has helped for you?[/SIZE]

[SIZE=2]Thank you in advance.[/SIZE][/SIZE]

Sincerely,

Adam

---

### Post by adamzendarski on 2013-12-18
Anyone?

---

### Post by oldfred on 2013-12-18
probably related to video. Have you tried bumblebee?

 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

      
 Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

Different brand but still dual video issues
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1)

---

### Post by adamzendarski on 2014-02-20
**Hi,**

I have found the solution that gets me _4 hours of battery life_ and _fixes all fan noise, heat, and battery drain problems_.

For future reference to anyone who has a similar problem, I have created the following guide:

**1.** ```
 **Run:** sudo gedit /etc/default/grub
**Change:** GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
**To:** GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vt.handoff=7 pcie_aspm=force acpi=noirq acpi_backlight=vendor dell_laptop.backlight=0 intel_iommu=off i915.powersave=1 i915.i915_enable_rc6=4 i915.lvds_downclock=1 i915.i915_enable_fbc=1 i915.semaphores=1 drm.vblankoffdelay=1 intel-audio-powersave=true acpi_osi=Linux"

```[B]

2. [/B]```
 **Run:** sudo add-apt-repository ppa:xorg-edgers/ppa; sudo apt-get update; sudo apt-get install bumblebee nvidia-331 nvidia-settings-331 xserver-xorg-video-intel

```

**3.** ```
 [B]
Run:[/B] sudo gedit /etc/bumblebee/bumblebee.conf
[B]
Change:[/B]
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia
[B]
To:[/B]
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia_331
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-331:/usr/lib32/nvidia-331
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-331/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia 

```

**4.** ```
 [B]
Run:[/B] sudo add-apt-repository ppa:webupd8team/unstable; sudo apt-get update; sudo apt-get install laptop-mode-tools fancontrol lm-sensors iotop smartdimmer cpufrequtils indicator-cpufreq powernap powerwake powertop acpi acpid acpi-call-tools apmd xapm

***Caution: **If you have TLP or PM-Utils, remove them FIRST.*

```

**5.** ```
 
**Run:** sudo lmt-config-gui
**Then:** Check all options in the box that pops up and click apply. 

```

At least that's how it worked for me with **DELL XPS 15z (L511z)** and **UBUNTU GNOME 13.10**.

[B]Sincerely,

Adam[/B]

---

