---
title: "No Additional Drivers listed for e555 lenovo thinkpad"
date: 2016-09-25
forum: Desktop Environments
---

### Post by Kilarin on 2016-09-25
I have a Lenovo ThinkPad Edge E555 20DH002QUS AMD Dual Core A6-7000
with Graphics adapter: AMD Radeon R5 (Kaveri), Core: 514 MHz, 14.201.1003.1001

I just upgraded from Xubuntu 14.04 32bit to Xubuntu 16.04 64bit.  (fresh install, of course)

Under 14.04 I went to "Additional Drivers" and switched from using "Video driver for the AMD graphics accelerators from xserver-xorg-video-ati(open source, tested)"
to "Video driver for the AMD graphics accelerators from fglrx-updates (proprietary)" and my graphics improved greatly.

After I installed 16.04 I figured I would do the same, BUT, when I go to "Additional Drivers" it says "No proprietary drivers are in use" so I'm assuming the fglrx-updates driver is not installed.  And then it brings up an entry for "Unknown: Unknown" "Using Processor microcode firmware for AMD CPUs from amd64-microcode (proprietary)"  (do not use the device is checked)

I'm just ignoring the microcode entry, but where are the additional video drivers?

I'm assuming I do NOT have the proprietary driver installed, right?  And if I am correct on that, why doesn't it show up in the "Additional Drivers" list, and how can I get it installed?

Info that might be helpful:
```

$  lspci | grep VGA 
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kaveri [Radeon R4 Graphics]

from /var/log/Xorg.0.log 
[    36.530] (II) LoadModule: "radeon"
[    36.531] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    36.659] (II) Module radeon: vendor="X.Org Foundation"
[    36.659]    compiled for 1.18.3, module version = 7.7.0
[    36.659]    Module class: X.Org Video Driver
[    36.659]    ABI class: X.Org Video Driver, version 20.0

$ sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Kaveri [Radeon R4 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:3000(size=256) memory:f0b00000-f0b3ffff memory:f0b60000-f0b7ffff

```

Thank you

---

### Post by kc1di on 2016-09-25
Hi Kilarin,
This is a past from the Ask Ubuntu site. 
> fglrx

The fglrx driver is now deprecated in 16.04, and we recommend its open source alternatives (radeon and amdgpu). AMD put a lot of work into the drivers, and we backported kernel code from Linux 4.5 to provide a better experience.

When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware).
In a mailing list discussion, it's suggested that people who really need the fglrx driver might have to continue using 14.04 until the open source driver improves:

AMD dropped support for their proprietary-blob fglrx video driver so it can't be included in 16.04 LTS. The last release AMD did can not be used because it is incompatible with the newer x.org display server. Most people will be able to the use the open source AMD video driver, but there are a few applications (certain graphics-intensive games, bitcoin mining) for which it is inadequate. Folk who rely on such applications might choose to remain on 14.04 LTS until adequate support lands in the open source AMD video drivers. 

It may shed some light on your question.

---

### Post by Kilarin on 2016-09-25
That explains it, thank you very much!

---

