---
title: "terminal always crashes X session 7.10 and 8.04.1"
date: 2008-08-22
forum: Desktop Environments
---

### Post by jeffk on 2008-08-22
A Compaq Presario 5BW135 (633Mhz Celeron) has a repeatable problem with xubuntu stock terminal app crashing the X session (goes to character mode, then returns to graphical login).

This had been happening with xubuntu 7.10, and with todays update to 8.04.1, I was surprised to find that it still happens. 

Terminal being such a core component, I can only expect this machine's problem to be a hardware interaction, so I'll list the short lspci and longer lshw output below. Please let me know if anything else about the system would be helpful to identify the problem.
```
$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
01:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0a.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
```
```

compaq
    description: Mini Tower Computer
    product: Compaq PC
    vendor: Compaq
    version: N/A
    serial: 1X07DTYF72XF
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=mini-tower uuid=31583037-4454-5946-3732-584620202020
  *-core
       description: Motherboard
       product: 06C0h
       vendor: Compaq
       physical id: 0
       version: None
       serial: None
     *-firmware
          description: BIOS
          vendor: Compaq
          physical id: 0
          version: 686C3 (06/20/2000)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.3
          slot: J1
          size: 633MHz
          capacity: 633MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 5
             size: 32KiB
             capacity: 32KiB
             capabilities: internal varies
        *-cache:1
             description: L2 cache
             physical id: 6
             size: 128KiB
             capacity: 512KiB
             capabilities: pipeline-burst synchronous internal varies
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 192MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous 83 MHz (12.0 ns)
             physical id: 0
             slot: DIMM1
             size: 64MiB
             width: 64 bits
             clock: 83MHz (12.0ns)
        *-bank:1
             description: DIMM DRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM2
             size: 128MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci
          description: Host bridge
          product: 82810E DC-133 (GMCH) Graphics Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810E DC-133 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: ES1988 Allegro-1
                vendor: ESS Technology
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=Maestro3 latency=64 maxlatency=24 mingnt=2 module=snd_maestro3
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 10
                serial: 00:50:fc:8c:90:4f
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=66 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
           *-communication
                description: Modem
                product: HSP MicroModem 56
                vendor: PCTel Inc
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm hayes_16450 cap_list
                configuration: driver=serial latency=0
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801AA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: QUANTUM FIREBALL
                vendor: Quantum
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: A03.
                serial: 174047310617
                size: 19GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9800481f
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 390d-9db3
                   size: 9060MiB
                   capacity: 9060MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 71390fda-0064-465e-8938-5b197a45400e
                   size: 9922MiB
                   capacity: 9922MiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-01-13 08:03:26 filesystem=ext3 modified=2008-08-22 20:47:06 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-22 20:47:06 state=mounted
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 486MiB
                   capacity: 486MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 486MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: CD-RW  CRX320EE
                vendor: SONY
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: RYK1
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: 82801AA SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by Diabolis on 2008-08-23
Maybe you'll find a clue in the X11 log:
```
cat /var/log/Xorg.0.log
```

---

### Post by jeffk on 2008-08-25
Here is the /var/log/Xorg.0.log output:
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux compaq 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 25 13:01:49 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Compaq MV740"
(**) |   |-->Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7124 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7125 card 0e11,b165 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:05:0: chip 125d,1988 card 0e11,b19d rev 12 class 04,01,00 hdr 00
(II) PCI: 01:09:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:0a:0: chip 134d,7897 card 134d,0001 rev 02 class 07,03,01 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0x40000000 - 0x400fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:1:0) Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller rev 3, Mem @ 0x44000000/26, 0x40100000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[1] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[2] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[4] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[7] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[8] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[1] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[2] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[3] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[4] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[5] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[6] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[7] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[8] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[13] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[14] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:01:0
(--) Chipset i810e found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[9] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[13] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[14] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[5] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[6] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[7] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[8] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[9] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[13] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[14] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[15] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[16] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[17] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[18] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[19] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(**) intel(0): Depth 24, (--) framebuffer bpp 24
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(WW) intel(0): DRI is disabled because it runs only at 16-bit depth.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 2.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel810(TM) Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 32.18
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: i810 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level 2
(II) intel(0): VESA VBE DDC transfer in appr. 1 sec.
(II) intel(0): VESA VBE DDC read successfully
(II) intel(0): Manufacturer: CPQ  Model: 3036  Serial#: 0
(II) intel(0): Year: 2000  Week: 24
(II) intel(0): EDID Version: 1.2
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) intel(0): Sync:  Separate
(II) intel(0): Max H-Image Size [cm]: horiz.: 33  vert.: 25
(II) intel(0): Gamma: 2.85
(II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) intel(0): redX: 0.612 redY: 0.353   greenX: 0.293 greenY: 0.595
(II) intel(0): blueX: 0.149 blueY: 0.068   whiteX: 0.281 whiteY: 0.311
(II) intel(0): Supported VESA Video Modes:
(II) intel(0): 720x400@70Hz
(II) intel(0): 640x480@60Hz
(II) intel(0): 640x480@75Hz
(II) intel(0): 800x600@60Hz
(II) intel(0): 800x600@75Hz
(II) intel(0): 1024x768@60Hz
(II) intel(0): 1024x768@75Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 640  vsize 480  refresh: 70  vid: 18993
(II) intel(0): #1: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) intel(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) intel(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) intel(0): #4: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): Ranges: V min: 50  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) intel(0): Monitor name: Compaq MV740
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff000e11363000000000
(II) intel(0): 	180a0102682119b9e8d1629c5a4b9826
(II) intel(0): 	11484fa54a00314a315945596159714f
(II) intel(0): 	81800101010100000003ea00e0812415
(II) intel(0): 	7b88dc04bc01df00000000fd0032781e
(II) intel(0): 	460b000a202020202020000080430021
(II) intel(0): 	000000000000000000000000000000fc
(II) intel(0): 	00436f6d706171204d563734300a009f
(II) intel(0): EDID vendor "CPQ", prod id 12342
(II) intel(0): DDCModeFromDetailedTiming: 3584x2048 Warning: We only handle seperate sync.
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 128x33 mode
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "3584x2048"x0.0    0.00  3584 4132 4153 6147  2048 2087 2098 2528 -hsync -vsync (0.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "640x480"x69.6   28.00  640 664 720 800  480 483 487 503 -hsync +vsync (35.0 kHz)
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(--) intel(0): Chipset: "i810e"
(--) intel(0): Linear framebuffer at 0x44000000
(--) intel(0): IO registers at addr 0x40100000
(II) intel(0): Kernel reported 38144 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 152572k available
(==) intel(0): Will alloc AGP framebuffer: 8192 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Compaq MV740: Using hsync range of 30.00-70.00 kHz
(II) intel(0): Compaq MV740: Using vrefresh range of 50.00-120.00 Hz
(II) intel(0): Compaq MV740: Using maximum pixel clock of 110.00 MHz
(II) intel(0): Clock range:   9.50 to 136.00 MHz
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (mode clock too high)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (insufficient memory for mode)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using driver mode "3584x2048" (insufficient memory for mode)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(--) intel(0): Virtual size is 1280x1024 (pitch 2048)
(**) intel(0): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) intel(0): *Driver mode "1152x864": 104.0 MHz, 67.7 kHz, 74.8 Hz
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(**) intel(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) intel(0): Modeline "1024x768"x84.9   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync (68.7 kHz)
(**) intel(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) intel(0): Modeline "800x600"x84.9   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync (53.7 kHz)
(**) intel(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) intel(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) intel(0): Modeline "640x480"x84.6   35.00  640 664 728 816  480 483 487 507 -hsync +vsync (42.9 kHz)
(**) intel(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) intel(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) intel(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(**) intel(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) intel(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(**) intel(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) intel(0): Modeline "1152x768"x54.8   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync (44.2 kHz)
(**) intel(0):  Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) intel(0):  Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) intel(0):  Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) intel(0):  Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) intel(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) intel(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) intel(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) intel(0):  Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) intel(0):  Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0):  Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) intel(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) intel(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) intel(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0):  Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) intel(0):  Driver mode "640x480": 28.0 MHz, 35.0 kHz, 69.6 Hz
(II) intel(0): Modeline "640x480"x69.6   28.00  640 664 720 800  480 483 487 503 -hsync +vsync (35.0 kHz)
(**) intel(0):  Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) intel(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) intel(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) intel(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) intel(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) intel(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) intel(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) intel(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) intel(0): Display dimensions: (330, 250) mm
(**) intel(0): DPI set to (98, 104)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0x40100000 - 0x4017ffff (0x80000) MS[B]
	[1] 0	0	0x44000000 - 0x47ffffff (0x4000000) MS[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0x40000000 - 0x400000ff (0x100) MX[B]
	[7] -1	0	0x40100000 - 0x4017ffff (0x80000) MX[B](B)
	[8] -1	0	0x44000000 - 0x47ffffff (0x4000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x00001800 - 0x0000183f (0x40) IX[B]
	[15] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000eee0 - 0x0000eeef (0x10) IX[B]
	[18] -1	0	0x0000eec0 - 0x0000eedf (0x20) IX[B]
	[19] -1	0	0x00002020 - 0x0000202f (0x10) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) intel(0): Write-combining range (0x44000000,0x4000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 109.1 MHz [ 0x30 0x9 0x20 ] [ 50 11 2 ]
(II) intel(0): chose watermark 0x22418000: (tab.freq 121.0)
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1024 pages failed
	(Cannot allocate memory)
(II) intel(0): No physical memory available for 4194304 bytes of DCACHE
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)
(II) intel(0): Allocated of 4096 bytes for HW cursor
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00801000 (pgoffset 2049)
(II) intel(0): Allocated of 16384 bytes for ARGB HW cursor
(II) intel(0): Adding 256 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Setting up tile and stipple cache:
		32 128x128 slots
		12 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(**) Option "dpms"
(**) intel(0): DPMS enabled
(WW) intel(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetKbdSettings - type: -1081672900 rate: 30 delay: 500 snumlk: 140
```

---

### Post by mali2297 on 2008-08-25
I too would have thought that they'd fixed this problem. The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

See also this post for a possible solution:
[http://ubuntuforums.org/showthread.php?t=605869?post=#8](http://ubuntuforums.org/showthread.php?t=605869?post=#8)

However, I suggest that you use another terminal emulator, like xterm (installed by default).

---

