---
title: "Problem with RGB in GLX"
date: 2006-07-19
forum: Desktop Environments
---

### Post by rogeriovinhal on 2006-07-19
Hi, I've made some other topics around the forum, but none of them could help me, and this bug is freaking me out.

I have installed Kubuntu 64 bits with the fglrx drivers. I've tried 3 fglrx drivers, including the one from the repos, and following carefully the HOWTOs, but I everytime have this problem:

glxinfo
```

roger@Roger:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 -1  0 r  y  . -1 -1  0  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 -1  0 r  y  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 -1  0 r  .  . -1 -1  8  0  0 16  8 16 16 16 16  1 0 None

```

fglrxinfo
```

roger@Roger:~$ fglrxinfo
Error: couldn't find RGB GLX visual!

```

Xorg.0.log
```
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.26.18
	ABI class: X.Org Server Extension, version 0.2
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000001f
(==) fglrx(0): cpuSpeedMHz: 0x000008a2
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): using built in AGPGART module: no
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf9000000 - 0xf900ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfb000000 - 0xfb003fff (0x4000) MX[B]
	[7] -1	0	0xfc001000 - 0xfc001fff (0x1000) MX[B]
	[8] -1	0	0xfc005000 - 0xfc0050ff (0x100) MX[B]
	[9] -1	0	0xfc004000 - 0xfc004fff (0x1000) MX[B]
	[10] -1	0	0xfc003000 - 0xfc003fff (0x1000) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xf9010000 - 0xf901ffff (0x10000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf9000000 - 0xf900ffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[31] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[32] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[33] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[35] -1	0	0x00009000 - 0x000090ff (0x100) IX[B](B)
	[36] 0	0	0xf80003b0 - 0xf80003bb (0xc) IS[B](OprU)
	[37] 0	0	0xf80003c0 - 0xf80003df (0x20) IS[B](OprU)
(II) fglrx(0): UMM Bus area:     0xd0954000 (size=0x076ac000)
(II) fglrx(0): UMM area:     0xd0954000 (size=0x076ac000)
(II) fglrx(0): driver needs X.org 6.8.x.y with x.y >= 99.8
(II) fglrx(0): detected X.org 7.0.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "UseFBDev" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 6988
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295
No matching visual for __GLcontextMode with visual class = 1 (32774), nplanes = 4294967295

```

I think this is a problem with the GLX in mesa, but I have reinstalled all the mesa packages and did no good...
Has anyone overcome this problem, and can plesae help me or give me some directions?

EDIT: Nevermind, I got it resolved. I had to move the SecurityPolicy file to a directory /etc/X11/xserver

---

