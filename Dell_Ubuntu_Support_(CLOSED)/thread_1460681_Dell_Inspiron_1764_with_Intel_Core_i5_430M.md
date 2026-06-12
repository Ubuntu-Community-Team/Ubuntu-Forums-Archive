---
title: "Dell Inspiron 1764 with Intel Core i5 430M"
date: 2010-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by baconman on 2010-04-23
I'm considering buying one of these. Will it work with 10.04? Will the onboard Intel video card work? As I understand it the Core i5 is a very new architecture.

I will probably run Kubuntu but I suppose that doesn't really matter as far as compatibility goes.

---

### Post by Kai Summers on 2010-04-23
The i5 is compatible. I know someone with a laptop with i5 core and running Ubuntu Lucid Lynx, and they have no issues with it. On the video driver front not to sure what is in his laptop...

---

### Post by baconman on 2010-04-23
Just to clarify: the i5 processor has an integrated graphics card but some laptops ship with a separate graphics card. The one I'm considering uses the integrated Intel graphics.

---

### Post by thinkbrowner on 2010-05-02
I bought one recently, and Ubuntu 10.04LTS has flawless video. There are only two problems with it, 1: you need to use an upstream kernel (I used [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-05-01-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-05-01-lucid/)) with the "acpi_sleep=sci_force_enable" tag to get it to resume from suspend, and 2: the Wifi driver needs to be custom compiled for it to work. Install the linux headers for the upstream kernel and install the  bcmwl-kernel-source package. It will compile it during installation. Then, run "echo wl|sudo tee -a /etc/modules".

---

### Post by dantheperson on 2010-05-17
FWIW i've got a 1764, and to get wireless working i just had to click System -> Administration -> Hardware Drivers

and then select the binary broadcom STA driver.  Not sure if you need to be on the net to access the driver, i was on wired ethernet and it did feel like it went out to the net.

Then just make sure the wireless is turned on.  I'm not sure how to tell if it's on or off, if the driver loads and you can't see any networks, just press F2 and try again.

I haven't looked at the suspend issue yet.

---

### Post by thinkbrowner on 2010-05-20
The standard Broadcom STA driver worked with the normal kernel. When I upgraded to the upstream kernel, it needed some tweaking.

---

### Post by dantheperson on 2010-05-24
Thanks for that info.  I've just done the kernel upgrade now to get sleep/resume working.

BTW full hibernate works fine, so i have just been using that instead till now.

Had some issues getting the wireless working so i'm posting here.
The short answer is use the version of the kernel thinkbrowner linked to and you'll have no problems.

The long answer if you want the latest and greatest follows:

Following the instructions at
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

download the latest image and headers for your architecture

In my case i downloaded from:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/)

these 3 files:
linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb	
linux-headers-2.6.34-020634_2.6.34-020634_all.deb
linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb

then from a commandline (dpkg -i <file>) or the GUI install them.

After a reboot you'll have to install the wireless drivers again.  But you'll find the standard lucid version of the dirvers no longer compiles against the newer kernel source.

This has been fixed see:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/580594](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/580594)

But the fix is not available for lucid. So you need to download the maveric drivers from:
[https://launchpad.net/ubuntu/+source/bcmwl/5.60.48.36+bdcom-0ubuntu4/+build/1740765](https://launchpad.net/ubuntu/+source/bcmwl/5.60.48.36+bdcom-0ubuntu4/+build/1740765)

Now reboot into the latest kernel and run:
sudo dpkg -i bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu4_amd64.deb 
sudo modprobe wl 

Now your netowrking is back, phew.

---

### Post by thinkbrowner on 2010-05-24
When I wrote that, the kernel version I linked to was the latest daily build. I'm reinstalling right now (very corrupted attempt at cross compiling) and I'm gonna try your version this time. Do you need to add the "acpi_sleep=sci_force_enable" switch to grub?

---

### Post by dantheperson on 2010-05-25
I do have that option set. Don't know if its still required, haven't  tried without

---

### Post by thinkbrowner on 2010-05-25
It is. I just tried coming out of standby without it. No Go.

---

### Post by Saghaulor on 2010-06-12
> **thinkbrowner said:**
> I bought one recently, and Ubuntu 10.04LTS has flawless video. There are only two problems with it, 1: you need to use an upstream kernel (I used [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-05-01-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2010-05-01-lucid/)) with the "acpi_sleep=sci_force_enable" tag to get it to resume from suspend, and 2: the Wifi driver needs to be custom compiled for it to work. Install the linux headers for the upstream kernel and install the  bcmwl-kernel-source package. It will compile it during installation. Then, run "echo wl|sudo tee -a /etc/modules".

Does your brightness toggle work? For me, the notification meter responds, but the actual brightness doesn't change.

I don't actually have the Dell, but I'm running the 430m chipset.

---

### Post by dantheperson on 2010-06-13
The brightness toggle works for me with the Dell 1764

---

### Post by Saghaulor on 2010-06-13
> **dantheperson said:**
> The brightness toggle works for me with the Dell 1764

Would you mind posting some details about your hardware and kernel/xorg versions?

```
uname -a
```
```
aptitude show xserver-xorg-core 
```
```
aptitude show xserver-xorg-video-intel
```

---

### Post by dantheperson on 2010-06-14
```
dantheperson@danski:~$ uname -a 
Linux danski 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
dantheperson@danski:~$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.6-2ubuntu7
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 4,989k
Depends: xserver-common (>= 2:1.7.6-2ubuntu7), xserver-xorg, udev (>= 149),
         libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
         libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>=
         147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Recommends: libgl1-mesa-dri (>= 7.1~rc1)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
           6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
           xserver-xorg-input-2.1, xserver-xorg-input-4,
           xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
           xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2,
           xserver-xorg-video-4, xserver-xorg-video-5
Replaces: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
          6.8.2-38)
Provides: xserver
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.

dantheperson@danski:~$ aptitude show xserver-video-intel
E: Unable to locate package xserver-video-intel
dantheperson@danski:~$ aptitude show xserver-xorg-video-intel
Package: xserver-xorg-video-intel
State: installed
Automatically installed: no
Version: 2:2.9.1-3ubuntu5
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,729k
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.11), libdrm2 (>= 2.4.3),
         libpciaccess0 (>= 0.8.0+git20071002), libxext6 (>= 0), libxfixes3 (>=
         1:4.0.1), libxv1, libxvmc1, xserver-xorg-core (>= 2:1.6.99.900)
Recommends: intel-gpu-tools
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
           2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
          xserver-xorg-video-i810 (< 2:1.9.91-1),
          xserver-xorg-video-i810-modesetting,
          xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-6
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides XvMC (XVideo Motion Compensation) drivers for
 i810/i815 and i9xx and newer chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

dantheperson@danski:~$ 
```

---

### Post by Saghaulor on 2010-06-14
> **dantheperson said:**
> ```
dantheperson@danski:~$ uname -a 
Linux danski 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
dantheperson@danski:~$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.6-2ubuntu7
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 4,989k
Depends: xserver-common (>= 2:1.7.6-2ubuntu7), xserver-xorg, udev (>= 149),
         libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
         libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>=
         147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Recommends: libgl1-mesa-dri (>= 7.1~rc1)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
           6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
           xserver-xorg-input-2.1, xserver-xorg-input-4,
           xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
           xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2,
           xserver-xorg-video-4, xserver-xorg-video-5
Replaces: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
          6.8.2-38)
Provides: xserver
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.

dantheperson@danski:~$ aptitude show xserver-video-intel
E: Unable to locate package xserver-video-intel
dantheperson@danski:~$ aptitude show xserver-xorg-video-intel
Package: xserver-xorg-video-intel
State: installed
Automatically installed: no
Version: 2:2.9.1-3ubuntu5
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,729k
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.11), libdrm2 (>= 2.4.3),
         libpciaccess0 (>= 0.8.0+git20071002), libxext6 (>= 0), libxfixes3 (>=
         1:4.0.1), libxv1, libxvmc1, xserver-xorg-core (>= 2:1.6.99.900)
Recommends: intel-gpu-tools
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
           2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
          xserver-xorg-video-i810 (< 2:1.9.91-1),
          xserver-xorg-video-i810-modesetting,
          xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-6
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides XvMC (XVideo Motion Compensation) drivers for
 i810/i815 and i9xx and newer chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

dantheperson@danski:~$ 
```

Weird, we have almost the exact same configuration. And yet you say your brightness levels are functioning properly?

> $ uname -a
Linux stephenaghaulor-laptop 2.6.34-020634-generic #020634 SMP Mon May 17 19:27:49 UTC 2010 x86_64 GNU/Linux
stephenaghaulor@stephenaghaulor-laptop:~$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.6-2ubuntu7
Priority: optional
Section: x11
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Uncompressed Size: 4,989k
Depends: xserver-common (>= 2:1.7.6-2ubuntu7), xserver-xorg, udev (>= 149),
         libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
         libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0 (>=
         147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Recommends: libgl1-mesa-dri (>= 7.1~rc1)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Conflicts: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
           6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
           xserver-xorg-input-2.1, xserver-xorg-input-4,
           xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
           xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2,
           xserver-xorg-video-4, xserver-xorg-video-5
Replaces: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
          6.8.2-38)
Provides: xserver
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.

stephenaghaulor@stephenaghaulor-laptop:~$ aptitude show xserver-xorg-video-intelPackage: xserver-xorg-video-intel
State: installed
Automatically installed: no
Version: 2:2.11.0-1ubuntu1~xup
Priority: optional
Section: x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,253k
Depends: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.13), libdrm2 (>= 2.4.17),
         libpciaccess0 (>= 0.8.0+git20071002), libx11-6 (>= 0), libx11-xcb1,
         libxcb-aux0 (>= 0.3.6), libxcb-dri2-0 (>= 0), libxcb1 (>= 0), libxext6,
         libxfixes3 (>= 1:4.0.1), libxv1, libxvmc1, xserver-xorg-core (>=
         2:1.6.99.900)
Conflicts: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
           2:1.9.91-1), xserver-xorg-video-i810-modesetting,
           xserver-xorg-video-intel-modesetting
Replaces: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
          xserver-xorg-video-i810 (< 2:1.9.91-1),
          xserver-xorg-video-i810-modesetting,
          xserver-xorg-video-intel-modesetting
Provides: xserver-xorg-video-6
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides XvMC (XVideo Motion Compensation) drivers for
 i810/i815 and i9xx and newer chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

stephenaghaulor@stephenaghaulor-laptop:~$

---

### Post by dantheperson on 2010-06-15
yup they work 100%.  Didn't have to do anything to get them working.  I was quite pleasantly surprised, having spent days getting this sort of stuff going last time i used linux on the desktop in the redhat 6 days

---

### Post by Saghaulor on 2010-06-16
> **dantheperson said:**
> yup they work 100%.  Didn't have to do anything to get them working.  I was quite pleasantly surprised, having spent days getting this sort of stuff going last time i used linux on the desktop in the redhat 6 days

Can you post this?

```
lspci
```

---

### Post by dantheperson on 2010-06-16
```


dantheperson@danski:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by Saghaulor on 2010-06-17
> **dantheperson said:**
> ```


dantheperson@danski:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
03:00.0 Network controller: Broadcom Corporation Device 4353 (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

I think that you may have a different chipset than I. That might be why you're working and I'm not.

> $ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
stephenaghaulor@stephenaghaulor-laptop:~$

---

### Post by Saghaulor on 2010-06-23
Now I'm getting somewhere.

There seems to be an issue with permissions on /proc/acpi/video/GFX0/DD02/brightness

After ```
sudo su
``` and then ```
echo 50 > /proc/acpi/video/GFX0/DD02/brightness
``` my brightness level changed.

See my post here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27)

---

### Post by thinkbrowner on 2010-07-15
I'm having no problem with brightness control, or any other keyboard control for that matter (wifi, volume, brightness, forward, backward, play)

---

### Post by thinkbrowner on 2010-07-23
The only problem I've had with this laptop is: When coming out of standby, the wifi takes forever to connect, and sometimes fails. Other than that, things have been ducky.

---

### Post by dantheperson on 2010-07-24
Yeah, it takes ages here too to find the WiFi, and when it connects, the icon shows no signal strength and a red exclamation mark, even though it's running fine.

---

### Post by thinkbrowner on 2010-07-24
The missing signal indicator only happens to me when I'm using a 5Ghz connection (ie. 802.11a). If i'm using a 2.4Ghz connection(ie. 802.11b,g,n) it just takes forever to connect. sometimes it will not connect, and will ask for the password again. If that happens, I have to turn off the wifi, count to 10, and turn it back on.

---

### Post by buildup on 2010-07-31
Bought mine and installed Lucid and runs OK.  Can't remember if I had to go to Hardware Drivers for wireless.  I am introducing a new problem to see if anyone has 1764 issues with instant and without warning power-off.  I run 2 VMWare guests that don't serverely tax the laptop.  But if I run a bunch of concurrent Firefox tabs with Flash panels, that causes Linux do do an INSTANT power down.  No messages, and no shutdown process.  Like the battery and adapter were unplugged.
If will happen with the VMWare machines running and causing about 30% CPU (approx since System Monitor is not really showing CPU per task),  When I run a few (about 5) Firefox tabs causing gtk-gnash to run as replacement for Flash, the CPU goes up and when Firefox is doing a lot for the Flash panels, or I am working on web-pages, the instant power-off happens.  I also ran over 20 tabs with Flash and no VMWare guests.  The CPU was 90%, mem was 2G of 4G and no swap.  Just a point, but in Win7 in same basic scenario, CPU was 25-35% and NEVER causes a problem with all I am describing running.  
As I write this I am stressing the machine with no VMWare guests and over 20 tabs with a few with autorefresh.  In about 1 minute, the laptop was powered off.  Is there a log entry or such I could search for to pass on?

---

### Post by thinkbrowner on 2010-08-01
I've never had a problem like that, and I run two virtual machines while watching flash video through Hulu desktop. Flash never presents a steady framerate, even if it's the only thing running. Maybe you got a defective laptop? It seems like it's shutting down when it heats up.

---

### Post by dantheperson on 2010-08-01
> **dantheperson said:**
> Thanks for that info.  I've just done the kernel upgrade now to get sleep/resume working.

BTW full hibernate works fine, so i have just been using that instead till now.


After the latest lucid kernel update to 2.6.32-24.38 i tried the ubuntu kernel again, and now suspend / resume is working on my 1764.  No need to manually update the kernel to 2.6.34.

---

### Post by thinkbrowner on 2010-08-01
Is that with or without the "acpi_sleep=sci_force_enable" kernel argument?

---

### Post by dantheperson on 2010-08-02
> **thinkbrowner said:**
> Is that with or without the "acpi_sleep=sci_force_enable" kernel argument?

It's with.  But i haven't tried without - maybe it works.

So anyone stumbling on this from d internet, to get suspend working on a Dell 1564/1764, run update manager to pull down the latest kernel, if it still doesn't work then try adding "acpi_sleep=sci_force_enable" to the commandline at boot.

To make this permanent add it to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

e.g. mine reads:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=sci_force_enable"

---

### Post by thinkbrowner on 2010-08-02
I don't know, nor do I feel like messing around with it. Maybe by the time 10.10 comes out they'll have the problem fixed without having to manually edit grub.cfg

---

### Post by thinkbrowner on 2010-08-03
that tip with the grub default commands just made my life easier.

---

### Post by thinkbrowner on 2010-09-20
Has anybody else had any issues pertaining to graphics recently? I just did a software update last week and now thing are goofed up. I tried to watch a 720p video in VLC, and it crashed the computer (I have a ram monitor at the bottom of the screen, and it was maxed out from about 500mb before VLC launched). I tried opening Eduke32 (a port of Duke Nukem 3D) and it crashed X.org (brought me to a screen that listed start-up stuff ie. NFS client started, sendmail started etc.). Most recently I tried to open up a small file in blender (~10mb) and it did the same thing as Eduke32.

Anybody else having problems?

---

### Post by dantheperson on 2010-09-21
All working fine here for now.

---

### Post by Enigmapond on 2010-09-21
> **dantheperson said:**
> It's with.  But i haven't tried without - maybe it works.

So anyone stumbling on this from d internet, to get suspend working on a Dell 1564/1764, run update manager to pull down the latest kernel, if it still doesn't work then try adding "acpi_sleep=sci_force_enable" to the commandline at boot.

To make this permanent add it to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub

e.g. mine reads:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=sci_force_enable"

WOW! Thanx for this! I was having this suspend issue. I didn't to the upstream update but just took the update from the repos today and added that line to GRUB...my suspend now works great! Other than that Lucid runs very stable on my 1764 and have had no additional issues!

:guitar:

---

### Post by thinkbrowner on 2010-10-28
OK, taking this thread a little off-course: I just spent 6 hours updating my BIOS. It's impossible to do in Ubuntu so you need a USB drive with syslinux on it, a FreeDOS floppy image, an obscure Dell-modified 16-bit version of "PHLASH16.exe", the Windows version of the BIOS updater, and WINE. I'm going to create a disk image of it to save everybody else the hassle.

---

### Post by Saghaulor on 2010-10-28
> **thinkbrowner said:**
> OK, taking this thread a little off-course: I just spent 6 hours updating my BIOS. It's impossible to do in Ubuntu so you need a USB drive with syslinux on it, a FreeDOS floppy image, an obscure Dell-modified 16-bit version of "PHLASH16.exe", the Windows version of the BIOS updater, and WINE. I'm going to create a disk image of it to save everybody else the hassle.

You're a better person than I.

I would have just built a windows partition to do the trick.

---

### Post by dantheperson on 2010-10-28
> **thinkbrowner said:**
> I just spent 6 hours updating my BIOS. It's impossible to do in Ubuntu 

1) Is there something special about this laptop that means it can't be flashed from linux?

Did you try the dell tools? [http://linux.dell.com/biosdisk/](http://linux.dell.com/biosdisk/)

I've used flashroom before on other motherboards [http://www.flashrom.org/Flashrom](http://www.flashrom.org/Flashrom)

2) Why did you need to flash the dell?  Anything you would recommend to other owners?

---

### Post by thinkbrowner on 2010-10-28
Dell doesn't distribute a raw HDR bios for this laptop. I have to extract a WPH file from the original installer which can't be used with the dell tools, or biosdisk. I've been having some weird issues with losing BIOS settings, so I thought that updating to A11(the latest version) might be helpful.

PS.Saghaulor: I can't get windows to boot off an external drive on this, and besides: DOS is more stable (and FreeDOS is free!)

---

### Post by thinkbrowner on 2010-11-26
I just reinstalled a fresh copy of Ubuntu 10.10, and guess what: no upstream kernel, no added grub commands, no nothing! it just worked! I love Ubuntu!

---

