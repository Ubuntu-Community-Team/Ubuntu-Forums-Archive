---
title: "Boot Splash Screen and Login Screen wrong Resolution"
date: 2009-05-23
forum: Desktop Environments
---

### Post by defenestratos on 2009-05-23
Hey guys and girls,

I have had a problem with my graphics since 8.04LTS 64 bit. The login screen (In my current 9.04 Gnome 64bit install) as well as the boot splash screen are in a higher resolution than my little 1024x768 laptop monitor can handle. This means it looks really unprofessional when it is booting because the ubuntu logo is massive and in the bottom right corner. Once I log in I have changed my screen resolution in Preferences-Appearances so that is no prob. It is just login screen and boot splash. Grub is the correct resolution.

Here is Xorg.0.log

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux hugo-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri May 22 23:07:44 2009
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
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] rev 1, Mem @ 0xa4000000/67108864, 0xe1000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched openchrome from file name openchrome.ids
(==) Matched openchrome for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
	compiled for 1.5.99.902, module version = 0.2.903
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
	K8M800/K8N800, PM800/PM880/CN400, P4M800Pro/VN800/CN700,
	K8M890/K8N890, P4M900/VN896/CN896, CX700/VX700, P4M890, VX800
(II) Primary Device is: PCI 01@00:00:0
(!!) VIA Technologies does not support this driver in any way.
(!!) For support, please refer to [http://www.openchrome.org/](http://www.openchrome.org/).
(!!) (development build, compiled on Fri Feb 13 08:36:21 2009)
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAPreInit
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) CHROME(0): VIAGetRec
(II) CHROME(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) CHROME(0): Depth 24, (--) framebuffer bpp 32
(==) CHROME(0): RGB weight 888
(==) CHROME(0): Default visual is TrueColor
(--) CHROME(0): Chipset: K8M800/K8N800
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 65536 kB
(II) CHROME(0): Setting up default chipset options.
(II) CHROME(0): VIASetupDefaultOptions
(II) CHROME(0): Reading config file...
(II) CHROME(0): Starting to parse config file options...
(==) CHROME(0): Shadow framebuffer is disabled.
(==) CHROME(0): Hardware acceleration is enabled.
(==) CHROME(0): Using XAA acceleration architecture.
(==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
(==) CHROME(0): GPU virtual command queue will be enabled.
(==) CHROME(0): DRI IRQ will be disabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
(==) CHROME(0): AGP DMA will be used for 2D acceleration.
(==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
(==) CHROME(0): Will not enable VBE modes.
(==) CHROME(0): VBE VGA register save & restore will not be used
	if VBE modes are enabled.
(==) CHROME(0): Xv Bandwidth check is enabled.
(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
(==) CHROME(0): Digital output bus width is 12 bits.
(==) CHROME(0): DVI Center is disabled.
(==) CHROME(0): Panel size is not selected from config file.
(==) CHROME(0): Panel will not be forced.
(==) CHROME(0): TV dotCrawl is disabled.
(==) CHROME(0): TV deflicker is set to 0.
(==) CHROME(0): No default TV type is set.
(==) CHROME(0): No default TV output signal type is set.
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xe1000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xe1200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) CHROME(0): Will not print VGA registers.
(==) CHROME(0): Will not scan I2C buses.
(II) CHROME(0): ...Finished parsing config file options.
(--) CHROME(0): Detected Mitac 8889.
(II) CHROME(0): Detected MemClk 5
(II) CHROME(0): ViaGetMemoryBandwidth
(II) CHROME(0): Detected TV standard: PAL.
(==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) CHROME(0): ViaI2CInit
(II) CHROME(0): ViaI2CBus1Init
(II) CHROME(0): I2C bus "I2C bus 1" initialized.
(II) CHROME(0): ViaI2cBus2Init
(II) CHROME(0): I2C bus "I2C bus 2" initialized.
(II) CHROME(0): ViaI2CBus3Init
(II) CHROME(0): I2C bus "I2C bus 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) CHROME(0): I2C device "I2C bus 1:E-EDID segment register" registered at address 0x60.
(II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
(II) CHROME(0): ViaOutputsDetect
(II) CHROME(0): Enabling panel from PCI-subsystem ID information.
(II) CHROME(0): VIATVDetect
(II) CHROME(0): ViaVT162xDetect
(II) CHROME(0): I2C device "I2C bus 3:VT162x" registered at address 0x40.
(--) CHROME(0): Detected VIA Technologies VT1622A/VT1623 TV Encoder
(II) CHROME(0): ViaTVInit
(II) CHROME(0): ViaVT162xInit
(II) CHROME(0): VT162xSave
(II) CHROME(0): VT1622DACSense
(--) CHROME(0): VT162x: Nothing connected.
(II) CHROME(0): ViaOutputsSelect
(II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
(II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x07
(II) CHROME(0): ViaOutputsSelect: Panel.
(WW) CHROME(0): Panel on K8M800, PM800 and VM800 is currently not supported.
(WW) CHROME(0): Using VBE to set modes to work around this.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) CHROME(0): initializing int10
(II) CHROME(0): Primary V_BIOS segment is: 0xc000
(II) CHROME(0): VESA BIOS detected
(II) CHROME(0): VESA VBE Version 3.0
(II) CHROME(0): VESA VBE Total Mem: 65536 kB
(II) CHROME(0): VESA VBE OEM: VIA K8N800


(II) CHROME(0): VESA VBE OEM Software Rev: 1.0
(II) CHROME(0): VESA VBE OEM Vendor: 
(II) CHROME(0): VESA VBE OEM Product: 
(II) CHROME(0): VESA VBE OEM Product Rev: 
(II) CHROME(0): Searching for matching VESA mode(s):
Mode: 101 (640x480)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 203
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 203
	LinNumberOfImagePages: 203
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 101
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 101
	LinNumberOfImagePages: 101
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (720x480)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 169
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 169
	LinNumberOfImagePages: 169
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 173 (720x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 175 (720x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 1b9 (720x540)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 145
	LinNumberOfImagePages: 145
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 1ba (720x540)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 72
	LinNumberOfImagePages: 72
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 1bb (720x540)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 540
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17c (720x576)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 720
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 145
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 720
	BnkNumberOfImagePages: 145
	LinNumberOfImagePages: 145
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17e (720x576)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1440
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 72
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1440
	BnkNumberOfImagePages: 72
	LinNumberOfImagePages: 72
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 17f (720x576)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2880
	XResolution: 720
	YResolution: 576
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 35
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2880
	BnkNumberOfImagePages: 35
	LinNumberOfImagePages: 35
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 103 (800x600)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 127
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 127
	LinNumberOfImagePages: 127
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 63
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 63
	LinNumberOfImagePages: 63
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 84
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 84
	LinNumberOfImagePages: 84
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 41
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 41
	LinNumberOfImagePages: 41
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 20
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 20
	LinNumberOfImagePages: 20
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 179 (1280x768)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 67
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 67
	LinNumberOfImagePages: 67
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 17a (1280x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 33
	LinNumberOfImagePages: 33
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 17b (1280x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (1280x1024)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 50
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 50
	LinNumberOfImagePages: 50
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13b (1400x1050)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1408
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 39
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1408
	BnkNumberOfImagePages: 39
	LinNumberOfImagePages: 39
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (1400x1050)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 2816
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 2816
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 13e (1400x1050)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 5600
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 5600
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 120 (1600x1200)
	ModeAttributes: 0x9f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 33
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 33
	LinNumberOfImagePages: 33
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 122 (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
*Mode: 124 (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0xa4000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 108 (80x60)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 160
	XResolution: 80
	YResolution: 60
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 254
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 254
	LinNumberOfImagePages: 254
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 102 (800x600)
	ModeAttributes: 0x1f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0xa000
	WinFuncPtr: 0xc000a4be
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 31
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 2
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 31
	LinNumberOfImagePages: 31
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
(II) CHROME(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) CHROME(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) CHROME(0): Unable to estimate virtual size
(II) CHROME(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) CHROME(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(--) CHROME(0): Virtual size is 1600x1200 (pitch 1600)
(**) CHROME(0): *Built-in mode "1600x1200"
(**) CHROME(0): *Built-in mode "1400x1050"
(**) CHROME(0): *Built-in mode "1280x1024"
(**) CHROME(0): *Built-in mode "1280x768"
(**) CHROME(0): *Built-in mode "1024x768"
(**) CHROME(0): *Built-in mode "800x600": 0.0 MHz, 37879.3 kHz, 60.8 Hz
(II) CHROME(0): Modeline "800x600"x60.8    0.00  800 0 0 0  600 0 0 0 (37879.3 kHz)
(**) CHROME(0): *Built-in mode "720x576"
(**) CHROME(0): *Built-in mode "720x540"
(**) CHROME(0): *Built-in mode "720x480"
(**) CHROME(0): *Built-in mode "640x480": 0.0 MHz, 31469.2 kHz, 60.4 Hz
(II) CHROME(0): Modeline "640x480"x60.4    0.00  640 0 0 0  480 0 0 0 (31469.2 kHz)
(==) CHROME(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) CHROME(0): VIAUnmapMem
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[25] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[26] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[27] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[28] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[29] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[30] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[31] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[32] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[33] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[34] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[35] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[36] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[37] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[38] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[39] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[40] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[41] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[42] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[43] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[44] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[45] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[46] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[47] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[48] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[49] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[50] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[51] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[52] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[53] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[54] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[55] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[56] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[57] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[58] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[59] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) CHROME(0): VIAScreenInit
(II) CHROME(0): VIAMapFB
(--) CHROME(0): mapping framebuffer @ 0xa4000000 with size 0x4000000
(--) CHROME(0): Frame buffer start: 0x7f4367997000, free start: 0x753000 end: 0x4000000
(II) CHROME(0): VIAMapMMIO
(--) CHROME(0): mapping MMIO @ 0xe1000000 with size 0x9000
(--) CHROME(0): mapping BitBlt MMIO @ 0xe1200000 with size 0x200000
(II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) CHROME(0): VIASave
(II) CHROME(0): Primary
(II) CHROME(0): Crtc...
(II) CHROME(0): TVSave...
(II) CHROME(0): VT162xSave
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(II) CHROME(0): Trying VBE Mode 1600x1200 (0xc124) Refresh 60.00:
(II) CHROME(0): ViaVbeSetRefresh
(II) CHROME(0): Active Device: 2
(II) CHROME(0): Refresh Rate Index: 0
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): - Blanked
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
(II) CHROME(0): [drm] framebuffer handle = 0xa4000000
(II) CHROME(0): [drm] added 1 reserved context for kernel
(II) CHROME(0): X context handle = 0x1
(II) CHROME(0): [drm] installed DRM signal handler
(II) CHROME(0): [dri] visual configs initialized.
(II) CHROME(0): [drm] register handle = 0xe1000000
(II) CHROME(0): [drm] framebuffer handle = 0xa4000000
(II) CHROME(0): [drm] mmio Registers = 0xe1000000
(II) CHROME(0): [dri] mmio mapped.
(II) CHROME(0): - Visuals set up
(II) CHROME(0): VIAInternalScreenInit
(II) CHROME(0): - B & W
(II) CHROME(0): CursorStart: 0x3fc0000
(II) CHROME(0): Using 3600 lines for offscreen memory.
(II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		24 256x256 slots
		13 512x512 slots
		32 8x8 color pattern slots
(==) CHROME(0): Backing store disabled
(II) CHROME(0): - Backing store set up
(II) CHROME(0): - SW cursor set up
(II) CHROME(0): VIAHWCursorInit
(II) CHROME(0): - Def Color map set up
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): - Palette loaded
(II) CHROME(0): DPMS enabled
(II) CHROME(0): - DPMS set up
(II) CHROME(0): - Color maps etc. set up
(II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0204
(II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
(II) CHROME(0): [drm] Trying to enable AGP fast writes.
(II) CHROME(0): [drm] drmAgpEnabled succeeded
(II) CHROME(0): [drm] agpAddr = 0xb0000000
(II) CHROME(0): [drm] agpBase = (nil)
(II) CHROME(0): [drm] agpAddr = 0xb0000000
(II) CHROME(0): [drm] agpSize = 0x01e00000
(II) CHROME(0): [drm] agp physical addr = 0x00000000
(II) CHROME(0): [dri] Using AGP.
(II) CHROME(0): [drm] Using 36113888 bytes for DRM memory heap.
(II) CHROME(0): [dri] Frame buffer initialized.
(II) CHROME(0): [DRI] installation complete
(II) CHROME(0): [dri] Kernel data initialized.
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): direct rendering enabled
(II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
(II) CHROME(0): Using default xfree86 memcpy for video.
(II) CHROME(0): [XvMC] Registering chromeXvMC.
(II) CHROME(0): [XvMC] Initialized XvMC extension.
(II) CHROME(0): - Done
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
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: Loaded and initialized /usr/lib/dri/unichrome_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) AT Translated Set 2 keyboard: xkb_layout: "de"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Video Bus: xkb_layout: "de"
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) CHROME(0): VIASwitchMode
(II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
(II) CHROME(0): VIAWriteMode
(WW) CHROME(0): Unable to determine the refresh rate, using 60.00. Please check your configuration.
(II) CHROME(0): Trying VBE Mode 1024x768 (0xc118) Refresh 60.00:
(II) CHROME(0): ViaVbeSetRefresh
(II) CHROME(0): Active Device: 2
(II) CHROME(0): Refresh Rate Index: 0
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIAAdjustFrame
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
(II) CHROME(0): VIALoadPalette
```

How can I change the resolution to my login screen and boot splash screen to 1024x768?

[http://ubuntuforums.org/showthread.php?t=866154](http://ubuntuforums.org/showthread.php?t=866154) shows what I tried to do about it.
It's got better now with 9.04 and the extremely disruptive screen distortions have gone but there is still the issue of my login screen being at a strange resolution.

If I sorted that out it would feel really good!```

```

---

### Post by directhex on 2009-05-23
Boot screen:

1) ensure /etc/usplash.conf has the correct xres and yres set
2) ensure /boot/grub/menu.lst has either no vga= setting anywhere, or if it does, that it's a vga= for 1024x768 (vga=792)

X:

Open /etc/X11/xorg.conf and make sure that for each SubSection "Display" that no resolutions beyond your screen are there, e.g.:
```
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
```

---

### Post by defenestratos on 2009-05-23
I edited usplash and indeed it was set to the wrong resolution. Haven't restarted yet so can't say if it worked or not. I went into xorg.conf and could not find the subsection. Can I just paste one in? Here is my xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by defenestratos on 2009-05-30
I did the things you suggested and now there is no boot splash screen and the log in window is still to big for the screen. 

Is there a way I must apply the changes? In Usplash it states
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1024
yres=768
```

So I ran update-initramfs and then rebooted but to no avail.

I don't seem to be getting very many suggestions. 
Would it make more sense if I broke the problems down and just dealt with the splash screen and opened another thread for the login window? Am I in the wrong forum section?

---

