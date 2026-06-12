---
title: "Beryl problems"
date: 2006-12-09
forum: Desktop Environments
---

### Post by mistajon on 2006-12-09
Hi all

I have an IBM Thinkpad R60 and ubuntu 6.10.  
Installed beryl and see the error "libGL warning: 3d driver claims to not support visual 0x5b"

I then have to login under the console and startx and then beryl seems to work? I dont understand?

Looks like the video is integrated Intel Graphics Media Accelerator (GMA) 950
How can I fix this?
Thanks
Jon

---

### Post by x64Jimbo on 2006-12-09
Have you configured your xorg.conf file according to the tutorials?

---

### Post by mistajon on 2006-12-11
I'm still not sure how to fix this.  I can still startx but it wont start on boot up

	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.6.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945GM found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4304000 - 0xe4307fff (0x4000) MX[B]
	[5] -1	0	0xe4301000 - 0xe43017ff (0x800) MX[B]
	[6] -1	0	0xedf00000 - 0xedf00fff (0x1000) MX[B]
	[7] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[8] -1	0	0xee444400 - 0xee4447ff (0x400) MX[B]
	[9] -1	0	0xee444000 - 0xee4443ff (0x400) MX[B]
	[10] -1	0	0xee240000 - 0xee243fff (0x4000) MX[B]
	[11] -1	0	0xee180000 - 0xee1fffff (0x80000) MX[B](B)
	[12] -1	0	0xee200000 - 0xee23ffff (0x40000) MX[B](B)
	o
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0xD0000000
(--) I810(0): IO registers at addr 0xEE100000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 7932 kB stolen memory.
(II) I810(0): Kernel reported 238592 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 954364 kB available
(II) I810(0): Monitoring connected displays enabled
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 12288 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 12288 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 7932 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1313
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2059)
(II) I810(0): Size of device LFP (local flat panel) is 1024 x 768
(II) I810(0): No active displays on Pipe A.
(II) I810(0): Currently active displays on Pipe B:
(II) I810(0): 	LFP (local flat panel)
(II) I810(0): Lowest common panel size for pipe B is 1024 x 768
(==) I810(0): Display is using Pipe B
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) I810(0): VESA VBE PanelID read successfully
(II) I810(0): PanelID returned panel resolution : 1024x768
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: LEN  Model: 4040  Serial#: 0
(II) I810(0): Year: 2005  Week: 0
(II) I810(0): EDID Version: 1.3
(II) I810(0): Digital Display Input
(II) I810(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.590 redY: 0.342   greenX: 0.319 greenY: 0.540
(II) I810(0): blueX: 0.152 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 640x480@60Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) I810(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) I810(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 54.2 MHz   Image Size:  304 x 228 mm
(II) I810(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) I810(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) I810(0):  LTN150XF-L03
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
Mode: 30 (640x480)
(II) I810(0): Generic Monitor: Using hsync range of 43.89-48.51 kHz
(II) I810(0): Generic Monitor: Using vrefresh value of 60.00 Hz
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(--) I810(0): Display dimensions: (300, 230) mm
(--) I810(0): DPI set to (86, 84)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xee200000 - 0xee23ffff (0x40000) MS[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MS[B]
	[2] 0	0	0xee100000 - 0xee17ffff (0x80000) MS[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe4304000 - 0xe4307fff (0x4000) MX[B]
	[8] -1	0	0xe4301000 - 0xe43017ff (0x800) MX[B]
	[9] -1	0	0xedf00000 - 0xedf00fff (0x1000) MX[B]
	[10] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[11] -1	0	0xee444400 - 0xee4447ff (0x400) MX[B]
	[12] -1	0	0xee444000 - 0xee4443ff (0x400) MX[B]
	[13] -1	0	0xee240000 - 0xee243fff (0x4000) MX[B]
	[14] -1	0	0xee180000 - 0xee1fffff (0x80000) MX[B](B)
	[15] -1	0	0xee200000 - 0xee23ffff (0x40000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xee100000 - 0xee17ffff (0x80000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] 0	0	0x00001800 - 0x00001807 (0x8) IS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000018e0 - 0x000018ff (0x20) IX[B]
	[25] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[26] -1	0	0x000018c0 - 0x000018c3 (0x4) IX[B]
	[27] -1	0	0x000018c8 - 0x000018cf (0x8) IX[B]
	[28] -1	0	0x000018c4 - 0x000018c7 (0x4) IX[B]
	[29] -1	0	0x000018d0 - 0x000018d7 (0x8) IX[B]
	[30] -1	0	0x00001810 - 0x0000181f (0x10) IX[B]
	[31] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[32] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[33] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[34] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[35] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 6144 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x37b9b000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x34570000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x34586000).
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf8d88000
(II) I810(0): [drm] mapped SAREA 0xf8d88000 to 0xb7a80000
(II) I810(0): [drm] framebuffer handle = 0xd0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 32 kB for the logical context at 0xffe2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 3072 kB for the back buffer at 0xf800000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
	(Cannot allocate memory)
(II) I810(0): Allocated 3072 kB for the depth buffer at 0xf400000.
(II) I810(0): Allocated 52992 kB for textures at 0x620000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 12833 pages failed
	(Cannot allocate memory)
(II) I810(0): 0x81ff148: Memory at offset 0x00020000, size 6144 kBytes
(II) I810(0): 0x81ffcc8: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x81ffcf0: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x81fe4ec: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81ff188: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81ffd18: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): 0x81ff320: Memory at offset 0x0ffe2000, size 32 kBytes
(II) I810(0): 0x81ff340: Memory at offset 0x0f800000, size 3072 kBytes
(II) I810(0): 0x81ff360: Memory at offset 0x0f400000, size 3072 kBytes
(II) I810(0): 0x81ff380: Memory at offset 0x00620000, size 52992 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xee100000
(II) I810(0): [drm] ring buffer = 0xd0000000
(II) I810(0): [drm] init sarea width,height = 1024 x 768 (pitch 1024)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0xd0020000
(II) I810(0): [drm] Back Buffer = 0xdf800000
(II) I810(0): [drm] Depth Buffer = 0xdf400000
(II) I810(0): [drm] textures = 0xd0620000
(II) I810(0): [drm] Initialized kernel agp heap manager, 54263808
(II) I810(0): [drm] dma control initialized, using IRQ 201
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xd0000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0ffe2000 (pgoffset 65506)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0f800000 (pgoffset 63488)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f400000 (pgoffset 62464)
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics Touchpad touchpad found
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-93.xkm
Synaptics DeviceOff called
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf8d88000 at 0xb7a80000
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)

---

