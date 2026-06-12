---
title: "Failed to load module &quot;nouveau&quot; (already loaded, -1217058309)"
date: 2012-09-04
forum: Desktop Environments
---

### Post by ronaldv on 2012-09-04
My Ubuntu 12.04-32bits often (but not always) fails to load the proper nouveau driver and then falls back to the vesa driver, giving a low resolution and no external screen. As said, if I am lucky it loads ok (1 out of 10 tries).

I have the 11.09-64bits version in dual-boot on the same laptop and this has no problem.

Any hints?

Details are:
```

Device: VGA compatible controller: NVIDIA Corporation G86 [GeForce 8400M GT] (rev a1)
Kernel: 3.2.0-29-generic-pae

X-server:

X.Org X Server 1.11.3
Release Date: 2011-12-16
[    77.710] X Protocol Version 11, Revision 0
[    77.710] Build Operating System: Linux 2.6.42-26-generic i686 Ubuntu
[    77.710] Current Operating System: Linux rasmussen 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686
[    77.711] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=2d4adc2a-6fff-4d5f-b437-8a3254431f19 ro
[    77.714] Build Date: 04 August 2012  01:51:24AM
[    77.714] xorg-server 2:1.11.4-0ubuntu10.7 (For technical support please see http://www.ubuntu.com/support) 


Error: 

[    78.330] (II) LoadModule: "nouveau"
[    78.330] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    78.330] (II) Module nouveau: vendor="X.Org Foundation"
[    78.330] 	compiled for 1.11.3, module version = 0.0.16
[    78.330] 	Module class: X.Org Video Driver
[    78.330] 	ABI class: X.Org Video Driver, version 11.0
[    78.330] (II) UnloadModule: "nouveau"
[    78.330] (II) Unloading nouveau
[    78.330] (II) Failed to load module "nouveau" (already loaded, -1217058309)


```

Full xorg.log is attached.

---

### Post by ronaldv on 2012-10-10
I am pretty sure now that the 'randomness' is related to the power-plug being plugged into the laptop. Without it it seems to ALWAYS boot correct. With the plug plugged it seems to NEVER boot correct.

---

