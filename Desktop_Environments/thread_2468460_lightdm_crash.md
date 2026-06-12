---
title: "lightdm crash"
date: 2021-10-30
forum: Desktop Environments
---

### Post by hiepvs on 2021-10-30
I'm using xubuntu 18.04, after everytimes that I reboot the xubuntu, a lightdm is crashed ```
_usr_sbin_lightdm.0.crash
```
My Xorg.0.log:
```

...
[    41.284] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    41.284] (II) intel: Driver for Intel(R) HD Graphics
[    41.284] (II) intel: Driver for Intel(R) Iris(TM) Graphics
[    41.284] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics
[    41.288] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20171023
[    41.288] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20171229-1 (Timo Aaltonen <tjaalton@debian.org>)
[    41.288] (II) intel(0): SNA compiled for use with valgrind
[    41.308] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
[    41.308] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[    41.308] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    41.308] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    41.308] (==) intel(0): RGB weight 888
[    41.308] (==) intel(0): Default visual is TrueColor
[    41.308] (**) intel(0): Option "TearFree" "true"
[    41.309] (II) intel(0): Output eDP1 has no monitor section
[    41.309] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    41.309] (II) intel(0): Enabled output eDP1
[    41.309] (II) intel(0): Output HDMI1 has no monitor section
[    41.309] (II) intel(0): Enabled output HDMI1
[    41.309] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    41.309] (II) intel(0): Output VIRTUAL1 has no monitor section
[    41.309] (II) intel(0): Enabled output VIRTUAL1
[    41.309] (--) intel(0): Output eDP1 using initial mode 1366x768 on pipe 0
[    41.309] (**) intel(0): TearFree enabled
[    41.309] (==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
[    41.309] (==) intel(0): DPI set to (96, 96)
...
```
 How to solve it? Thanks

---

