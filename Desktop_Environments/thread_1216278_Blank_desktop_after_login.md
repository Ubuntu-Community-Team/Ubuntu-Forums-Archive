---
title: "Blank desktop after login"
date: 2009-07-18
forum: Desktop Environments
---

### Post by ssatoor on 2009-07-18
I have installed Ubuntu 8.10. After logging in I get a blank screen with only the cursor displayed. The cursor moves when I move the mouse. But no other menus or icons appear.

What could be the problem?

I checked the X conf file. But I did not know if that is the problem or how I should modify it.

I think it is trying to bring up the GNOME desktop.

Under /var/log - I find some error message about some infinite loop.

---

### Post by ~sHyLoCk~ on 2009-07-18
> **ssatoor said:**
> I have installed Ubuntu 8.10. After logging in I get a blank screen with only the cursor displayed. The cursor moves when I move the mouse. But no other menus or icons appear.

What could be the problem?

I checked the X conf file. But I did not know if that is the problem or how I should modify it.

I think it is trying to bring up the GNOME desktop.

Under /var/log - I find some error message about some infinite loop.

Post the error message in [pastebin](www.pastebin.com).

---

### Post by ssatoor on 2009-07-24
I have now disabled X11 on startup. But on normal bootup the screen is still blank.
 
If I boot in recovery mode & than continue normal reboot - the bootup is proper & I get the login prompt & I can login. But when I try to start X using startx - I get some garbled screen initially, than it turns blank.
 
My system has a Intel 845G integrated graphics chipset. I found mention of following problem:
"There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None"."
 
Could this be my problem? But I am not able to change this setting? Nothing happens when I press F4 at startup screen.
 
I see following in Xorg.0.log:
(II) intel(0): Setting screen physical size to 443 x 249
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x3ffe0001 getbl_err: 0x00000021
ipeir: 0x00000000 iphdr: 0x54f00006
LP ring tail: 0x000064c0 head: 0x000064e4 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0010 emr: 0xff7b
instdone: 0xff41 instpm: 0x0000
memmode: 0x00000000 instps: 0x00000031
hwstam: 0xfffe ier: 0x0002 imr: 0x053c iir: 0x0080
Ring at virtual 0xaf91b000 head 0x64e4 tail 0x64c0 count 32759
.
.
Ring at virtual 0xaf91b000 head 0x64e4 tail 0x64c0 count 32759
Ring end
space: 28 wanted 32
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8d4c000 at 0xb7b8c000
(II) intel(0): [drm] Closed DRM master.
Fatal server error:
lockup
(II) AIGLX: Suspending AIGLX clients for VT switch
Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb80bb400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b307bf]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b32a23]
4: /usr/bin/X11/X [0x80d6b0a]
5: /usr/lib/xorg/modules/extensions//libglx.so [0xb7becbe9]
6: /usr/bin/X11/X(AbortDDX+0x79) [0x80a8b09]
7: /usr/bin/X11/X(AbortServer+0x28) [0x813c498]
8: /usr/bin/X11/X(FatalError+0x63) [0x813caa3]
9: /usr/lib/xorg/modules/drivers//intel_drv.so(I830WaitLpRing+0x201) [0xb7b271d1]
10: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b4fba8]
11: /usr/lib/xorg/modules//libexa.so(exaFillRegionTiled+0x36f) [0xb7a3317f]
12: /usr/lib/xorg/modules//libexa.so [0xb7a336a8]
13: /usr/bin/X11/X [0x8177a94]
14: /usr/bin/X11/X(miPaintWindow+0x231) [0x8110991]
15: /usr/bin/X11/X(miWindowExposures+0x142) [0x8110d02]
16: /usr/lib/xorg/modules/extensions//libdri.so(DRIWindowExposures+0x97) [0xb7b9be17]
17: /usr/bin/X11/X [0x80d84ff]
18: /usr/bin/X11/X(MapWindow+0x303) [0x8077513]
19: /usr/bin/X11/X(InitRootWindow+0x100) [0x8077760]
20: /usr/bin/X11/X(main+0x416) [0x8071cb6]
21: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cc4685]
22: /usr/bin/X11/X [0x8071101]
Saw signal 11. Server aborting.
(II) AIGLX: Suspending AIGLX clients for VT switch
 
 
 
Any idea what I can try?
 
Thanks,
Sanjiv

---

