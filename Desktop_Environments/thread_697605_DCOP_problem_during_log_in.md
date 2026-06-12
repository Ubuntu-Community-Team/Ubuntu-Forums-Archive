---
title: "DCOP problem during log in"
date: 2008-02-15
forum: Desktop Environments
---

### Post by knichel on 2008-02-15
There was a problem loading the interprocess communications for KDE.  The error returned was...

```
Could not read connection list.
/home/stahlmanz/.DCOPserver_ws-12__0

Please check that the "dcopserver" program is running
```.


While the user was logging in to this workstation, I ran 
	tail -f  /var/log/Xorg.0.log 

and captured the following... But I do not understand what it means...
I have deleted everything in /tmp and /var/tmp that belongs to this user and still he cannot login.  There is no ~/.DCOPserver... file getting created in his home dir.

```
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf8d34000 at 0xb7b30000
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
        the saved state
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 7872 kB
(II) I810(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 256 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 10240 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xdfff000 (0x11b89000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xdffb000 (0x051b0000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xdffa000 (0x04972000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xdfea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] DRM interface version 1.3
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf8d34000
(II) I810(0): [drm] mapped SAREA 0xf8d34000 to 0xb7b30000
(II) I810(0): [drm] framebuffer handle = 0xe0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Not enabling the DRM memory manager.
(II) I810(0): Allocated 32 kB for the logical context at 0xdfe2000.
(II) I810(0): Allocated 6144 kB for the back buffer at 0xd000000.
(II) I810(0): Allocated 6144 kB for the depth buffer at 0xc800000.
(II) I810(0): Allocated 42752 kB for textures at 0xa20000
(II) I810(0): 0x81f60b0: Memory at offset 0x00020000, size 10240 kBytes
(II) I810(0): 0x84647c0: Memory at offset 0x0dfff000, size 4 kBytes
(II) I810(0): 0x85af538: Memory at offset 0x0dffb000, size 16 kBytes
(II) I810(0): 0x83b03fc: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81f60f0: Memory at offset 0x0dfea000, size 64 kBytes
(II) I810(0): 0x839de00: Memory at offset 0x0dffa000, size 4 kBytes
(II) I810(0): 0x81f6288: Memory at offset 0x0dfe2000, size 32 kBytes
(II) I810(0): 0x81f62a8: Memory at offset 0x0d000000, size 6144 kBytes
(II) I810(0): 0x81f62c8: Memory at offset 0x0c800000, size 6144 kBytes
(II) I810(0): 0x81f62e8: Memory at offset 0x00a20000, size 42752 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xfeb00000
(II) I810(0): [drm] ring buffer = 0xe0000000
(II) I810(0): [drm] init sarea width,height = 1024 x 768 (pitch 2048)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0x2c004000
(II) I810(0): [drm] Back Buffer = 0xed000000
(II) I810(0): [drm] Depth Buffer = 0xec800000
(II) I810(0): [drm] textures = 0xe0a20000
(II) I810(0): [drm] Initialized kernel agp heap manager, 43778048
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xe0000000,0x10000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0dfff000 (pgoffset 57343)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0dffb000 (pgoffset 57339)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0dfea000 (pgoffset 57322)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0dffa000 (pgoffset 57338)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0dfe2000 (pgoffset 57314)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0d000000 (pgoffset 53248)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0c800000 (pgoffset 51200)
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is disabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now disabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(II) I810(0): Initializing HW Cursor
(**) I810(0): DPMS enabled
(II) I810(0): Set up overlay video
(II) I810(0): Set up textured video
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): [drm] dma control initialized, using IRQ 16
(II) I810(0): direct rendering: Enabled
(II) I810(0): RandR enabled, ignore the following RandR disabled message.
(II) I810(0): Rotating to 0 degrees
(--) RandR disabled
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
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

Can someone please assist.  I need to get this person logged in again. 

--
JuJuBee

---

