---
title: "Windows Behavior 'Altered' in Ubuntu Lucid on laptop with ATI Mobility Radeon 9600"
date: 2010-05-21
forum: Desktop Environments
---

### Post by BlueInkAlchemist on 2010-05-21
I have a confession to make, fellows.

In my over-zealousness to address the issue I've been having running [World of Warcraft through Wine]("http://ubuntuforums.org/showthread.php?t=1488387"), I obliterated the fglrx folder from my system.  Now, the windows have stopped behaving properly.

The OS still loads, I'm able to log in, but the windows that I open no longer have a title bar or any of the relevant buttons - close, minimize, etc.  I'm also unable to alt-tab between them, and apparently this little system alteration I buggered reduced me from four desktops to one.  When trying to launch the Windows management tool from the GUI, I get the following error:

```
Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool
```

How do I restore this functionality?  More to the point, what's the best video driver I should be using that actually supports my laptop's GPU?  The current fglrx apparently no longer does that, and my attempts to install a legacy version failed.  I continued to get either "no supported adapters" or an error related to xorg.conf, which Lucid shouldn't be using anyway as far as I can tell.

This might help in the diagnostics of my problem:

```
$ lspci -v
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
	Subsystem: Dell Device 0191
	Flags: bus master, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: d0000000-dfffffff
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf80 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf40 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at bf20 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=06, sec-latency=32
	I/O behind bridge: 0000d000-0000efff
	Memory behind bridge: f6000000-fbffffff
	Prefetchable memory behind bridge: 30000000-33ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Memory at 34000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 0, IRQ 7
	I/O ports at b800 [size=256]
	I/O ports at bc40 [size=64]
	Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
	Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
	Subsystem: Conexant Systems, Inc. Device 5422
	Flags: medium devsel, IRQ 7
	I/O ports at b400 [size=256]
	I/O ports at b080 [size=128]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
	Subsystem: Dell Device 2001
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fc000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb, radeon

02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
	Subsystem: Dell Device 8127
	Flags: bus master, fast devsel, latency 32, IRQ 11
	Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: b44
	Kernel modules: b44

02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 168, IRQ 11
	Memory at f6000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 38000000-3bfff000
	I/O window 0: 0000d000-0000d0ff
	I/O window 1: 0000d400-0000d4ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10)
	Subsystem: Dell Device 0191
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at faffd800 (32-bit, non-prefetchable) [size=2K]
	Memory at faff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
	Subsystem: Intel Corporation Device 2721
	Flags: bus master, medium devsel, latency 32, IRQ 7
	Memory at faffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ipw2200
	Kernel modules: ipw2200
```

Any help you could offer in this would be appreciated.  Thank you in advance!

---

### Post by BlueInkAlchemist on 2010-05-23
Me again.  I managed to remove the proprietary drivers and opted instead for the open-source 'radeon' driver.  The driver itself is installed, but I have encountered the following problem:

```
~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I followed the steps [here]("http://www.x.org/wiki/radeonBuildHowTo") to install Mesa3D but rendering is still listed as "none" by compiz-check:

```


Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

Xorg's log:
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux josh-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=0d85b3aa-755b-4e49-aea0-12b4689d6461 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 23 18:05:27 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:4e50:1028:2001 ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] rev 0, Mem @ 0xd0000000/268435456, 0xfcff0000/65536, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(WW) Warning, couldn't open module dri
(II) UnloadModule: "dri"
(EE) Failed to load module "dri" (module does not exist, 0)
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(II) [KMS] No DRICreatePCIBusID symbol, no kernel modesetting.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): TOTO SAYS 00000000fcff0000
(II) RADEON(0): MMIO registers at 0x00000000fcff0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP)" (ChipID = 0x4e50)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): AGP card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 20000, max_out_pll: 35000, min_in_pll: 40, max_in_pll: 3000, xclk: 24300, sclk: 337.000000, mclk: 243.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=6 min=20000 max=35000; xclk=24300
(II) RADEON(0): External TMDS Table revision: 2
(II) RADEON(0): I2C bus "DVO" initialized.
(II) RADEON(0): I2C device "DVO:RADEON DVO Controller" registered at address 0x70.
(II) RADEON(0): Panel ID string: Y0316154X1
            
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71250
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 23, VOverPlus: 2, VSyncWidth: 6
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: NTSC
(II) RADEON(0): TV standards supported by chip: NTSC 
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC1
  DDC reg: 0x60
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DVO1
  DDC reg: 0x64
(II) RADEON(0): Port2:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x1b0
(II) RADEON(0): Port3:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
finished output detect: 1
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
finished output detect: 2
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 3
finished all detect
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.1   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x800
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1920
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 6909
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0x07ff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
(II) RADEON(0): Largest offscreen area available: 1280 x 6901
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Set up textured video
disable primary dac
disable FP2
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable primary dac
disable FP2
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
(II) RADEON(0): Setting screen physical size to 338 x 211
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event5)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event6)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event6"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event7)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event7"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
disable LVDS
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x07ff0000 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe7ffe000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Open ACPI successful (/var/run/acpid.socket)
disable primary dac
disable FP2
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xd7ffd000 0x07ff0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable primary dac
disable FP2
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) Video Bus: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Sleep Button: Device reopened after 1 attempts.
(II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
(II) PS/2 Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3158  Serial#: 0
(II) RADEON(0): Year: 2003  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 71.2 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  Y0316154X1
(II) RADEON(0):  Å¯žŽr`@
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3583100000000
(II) RADEON(0): 	000d0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101d51b00a0502017303020
(II) RADEON(0): 	26004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026400000000fe0059
(II) RADEON(0): 	303331360731353458310a20000000fe
(II) RADEON(0): 	00c5af9e8e72604000010a2020200052
(II) RADEON(0): EDID vendor "SEC", prod id 12632
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
disable LVDS
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x07ff0000 0xd7ffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xe7ffe000
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) PS/2 Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

---

### Post by texaswriter on 2010-05-23
From a terminal: metacity --replace

See if that corrects your issue. You really shouldn't "manually" delete a folder like that. There are ways to uninstall the fglrx drivers, especially if you installed the ones in the repository.

---

### Post by BlueInkAlchemist on 2010-05-24
> **texaswriter said:**
> From a terminal: metacity --replace

While metacity --replace didn't directly fix the issue, I did come across a solution that repaired the situation.  I reinstalled a few components and reconfigured xserver. It seems to be much better behaved now, and it's just a matter of getting World of Warcraft working...

---

### Post by texaswriter on 2010-05-24
Great!! :popcorn::guitar::P:):KS

Can you put "SOLVED" in the title of the original post so people know that it is resolved.

---

### Post by BlueInkAlchemist on 2010-05-24
> **texaswriter said:**
> Great!! :popcorn::guitar::P:):KS

Can you put "SOLVED" in the title of the original post so people know that it is resolved.

My pleasure.  Had to shorted the title to get the good news in there, but hopefully this will be helpful to other folks who find their windows title bars disappearing &c. :KS

---

