---
title: "Gnome (with compiz) locking up and sending me back to login after a couple of hours"
date: 2009-06-05
forum: General Help
---

### Post by stwschool on 2009-06-05
Any ideas guys? I'm on a fairly vanilla 9.04 ubuntu, albeit with gnome-do docky, compiz doing its thing, conky and wine running football manager frequently. About 2 hours into a session, the last couple of nights, it's kicked me back out to the login screen, and when logging back in performance is degraded as hell, suggesting to me that I'm logged in twice or that X is being a dog. Any ideas?

---

### Post by jenkinbr on 2009-06-06
First, I might try installing any and all updates.  There was a warning in the Jaunty Release notes stating that X would lock up in such a manner.

If that doesn't solve your issue, post the output of ```
dmesg | tail -30
``` after that problem happens.

---

### Post by stwschool on 2009-06-06
Thanks for the tip, I hadn't seen that. Looks like it was Emerald doing the damage, as after switching back to metacity the problem seems to have stopped. Buggered if I know why though :(

---

### Post by stwschool on 2009-06-06
Ok not so good. It's done it again. Time to try openbox and see if that helps.. Here's that output btw if you've got any ideas.

[   20.953587] vboxdrv: Found 4 processor cores.
[   20.953694] vboxdrv: fAsync=0 offMin=0x4ad offMax=0x1f38
[   20.953727] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.953728] vboxdrv: Successfully loaded version 2.2.4 (interface 0x000a0009).
[   22.831880] ppdev: user-space parallel port driver
[   26.431852] forcedeth 0000:00:0f.0: irq 2299 for MSI/MSI-X
[   26.432046] eth0: no link during initialization.
[   26.432480] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  815.947180] Too big adjustment 32
[  816.003848] Too big adjustment 32
[  871.191601] Too big adjustment 32
[  871.249137] Too big adjustment 32
[  921.990677] Too big adjustment 32
[  922.046534] Too big adjustment 32
[ 1012.370171] Too big adjustment 32
[ 1012.426865] Too big adjustment 32
[ 1332.712719] Too big adjustment 32
[ 1332.770735] Too big adjustment 32
[ 1674.144023] usb 2-1: new full speed USB device using ohci_hcd and address 3
[ 1674.366058] usb 2-1: configuration #1 chosen from 1 choice
[ 1674.473871] cdc_acm 2-1:1.1: ttyACM0: USB ACM device
[ 1674.478202] usbcore: registered new interface driver cdc_acm
[ 1674.478205] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 1674.570742] usbcore: registered new interface driver cdc_ether
[ 1674.575208] usb 2-1: bad CDC descriptors
[ 1674.575224] usbcore: registered new interface driver rndis_host
[ 1674.582248] usb 2-1: bad CDC descriptors
[ 1674.582265] usbcore: registered new interface driver rndis_wlan
[ 1688.287974] PPP BSD Compression module registered
[ 1688.312198] PPP Deflate Compression module registered

---

### Post by jenkinbr on 2009-06-06
dmesg didn't appear to provide anything useful

Let's see what your xorg.0.log file contains after this happens:

```
cat /var/log/xorg.0.log
```

Also, please use [noparse]```

```[/noparse] tags when posting output

---

### Post by stwschool on 2009-06-07
Just happened again so this time some better data..

dmesg | tail -30
```

[ 4429.090303] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 4429.093158] sd 9:0:0:0: [sdg] 63037440 512-byte hardware sectors: (32.2 GB/30.0 GiB)
[ 4429.094302] sd 9:0:0:0: [sdg] Write Protect is off
[ 4429.094306] sd 9:0:0:0: [sdg] Mode Sense: 23 00 00 00
[ 4429.094308] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 4429.094313]  sdg: sdg1 sdg2 < sdg5 sdg6 >
[ 4432.112232] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[ 4432.112327] sd 9:0:0:0: Attached scsi generic sg7 type 0
[ 4437.476555] kjournald starting.  Commit interval 5 seconds
[ 4437.476571] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[ 4437.483858] EXT3 FS on sdg6, internal journal
[ 4437.483864] EXT3-fs: mounted filesystem with ordered data mode.
[ 4572.476174] usb 1-7: USB disconnect, address 7
[ 4572.484056] Buffer I/O error on device sdg6, logical block 2851333
[ 4572.484059] lost page write due to I/O error on sdg6
[ 4572.484065] Aborting journal on device sdg6.
[ 4572.484072] Buffer I/O error on device sdg6, logical block 2851328
[ 4572.484074] lost page write due to I/O error on sdg6
[ 4572.484085] journal commit I/O error
[ 4572.510515] ext3_abort called.
[ 4572.510519] EXT3-fs error (device sdg6): ext3_put_super: Couldn't clean up the journal
[ 4572.510522] Remounting filesystem read-only
[10093.540789] NVRM: Xid (0002:00): 6, PE0001 
[10093.671556] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.695064] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.715755] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.736372] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.757102] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.778453] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002
[10093.799283] NVRM: Xid (0002:00): 13, 0001 00000000 00005039 00000328 00000000 00000002

```


cat /var/log/Xorg.0.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ryan-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  7 17:18:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@2:0:0) nVidia Corporation GeForce 9800 GTX rev 162, Mem @ 0xec000000/16777216, 0xd0000000/268435456, 0xea000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX/9800 GTX+ (G92) at PCI:2:0:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.5d.00.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800 GTX/9800 GTX+ at
(--) NVIDIA(0):     PCI:2:0:0:
(--) NVIDIA(0):     HP w1907 (CRT-0)
(--) NVIDIA(0): HP w1907 (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB Optical Mouse: Found 8 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0


```

First section seems to hint at a hard drive snafu. What do you think? SDA is the main HD right? So I'm guessing SDG is my external Maxtor 1tb hd, but that's formatted NTFS not ext3 as I recall. Main linux partition is ext4 btw.

---

### Post by stwschool on 2009-06-07
```
ryan@ryan-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc1010039

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   163589894    81793923+   7  HPFS/NTFS
/dev/sda2       163589895   173357414     4883760    5  Extended
/dev/sda3       173357415   625137344   225889965   83  Linux
/dev/sda5       163589958   173357414     4883728+  82  Linux swap / Solaris

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf23ee877

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  1953520064   976760001    7  HPFS/NTFS

```

My theory about the maxtor 1tb drive looks wrong then, not sure what sdg is... Nothing in /dev/ saying sdg (only goes up to sdf)

---

