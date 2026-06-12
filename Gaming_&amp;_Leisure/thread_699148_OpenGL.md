---
title: "OpenGL"
date: 2008-02-17
forum: Gaming &amp; Leisure
---

### Post by msjones on 2008-02-17
Hi,

I am wanting to install a few games native to linux. Mainly doom 3 UT etc.

I have just tried to install the Quake Wars demo. When I go to run the launcher I get this error:

```
ETQW 1.4.12343.12343  linux-x86 Jan 16 2008 10:19:41
found interface lo - loopback
found interface eth14 - 10.0.10.9/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/msjones/.quakewars/base/game000.pk4 with checksum 0x18457bb4
Loaded pk4 /home/msjones/.quakewars/base/game002.pk4 with checksum 0x40b37d8a
Loaded pk4 /home/msjones/.quakewars/base/pak000.pk4 with checksum 0xb920556e
Loaded pk4 /home/msjones/.quakewars/base/pak001.pk4 with checksum 0x452281ea
Loaded pk4 /home/msjones/.quakewars/base/pak002.pk4 with checksum 0x4082d93f
Loaded pk4 /home/msjones/.quakewars/base/zpak_english000.pk4 with checksum 0x99854ebc
Current search path:
/home/msjones/.etqwcl/base
/home/msjones/.quakewars/base
/home/msjones/.quakewars/base/zpak_english000.pk4 (755 files)
/home/msjones/.quakewars/base/pak002.pk4 (654 files)
/home/msjones/.quakewars/base/pak001.pk4 (1122 files)
/home/msjones/.quakewars/base/pak000.pk4 (6064 files)
/home/msjones/.quakewars/base/game002.pk4 (3 files)
/home/msjones/.quakewars/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------

Running in restricted mode.

----- Initializing Decls -----
Decompressing the global token cache...3006Kb
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
execing 'autoexec.cfg'
Vendor: Device:
/proc/cpuinfo CPU frequency: 2000.06 MHz
parse /proc/cpuinfo for CPU information
2 logical, 1 physical CPU(s)
detecting video ram (set sys_videoRam on command line to override) ..
trying /proc/dri/0/umm
Detected
        1 2.00 GHz CPU
        2032 MB of System memory
        256 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1680x1050
execing 'specs/minspec.dat'
execing 'specs/minspec_cpu.dat'
execing 'specs/minspec_gamedetail.dat'
execing 'specs/minspec_gpu.dat'
execing 'specs/minspec_gpudetail.dat'
execing 'specs/minspec_lighting.dat'
execing 'specs/minspec_foliage.dat'
Vendor: Device:
execing 'specs/minspec_foliage.dat'
Opening IP socket: localhost:-1
SDL_ListModes:
1680x1050 SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
thread priority set to 1
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
1 pixels multisampling
vsync: SDL reports -1074340712 - broken?
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
X..GL_EXT_texture_lod not found
X..GL_1.4_texture_lod_bias not found
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_ARB_texture_rectangle not found
X..GL_EXT_texture_rectangle not found
X..GL_EXT_stencil_wrap not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..GL_EXT_depth_bounds_test not found
X..GL_ARB_point_sprite not found
X..GL_ARB_occlusion_query not found
X..GL_EXT_framebuffer_object not found
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
X..GL_ARB_multisample not found
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
X..GL_ARB_shadow not found
X..GL_ARB_depth_texture not found
X..GL_EXT_gpu_program_parameters not found
0x0
[0x082e2cc1]
[0x0819fcdf]
[0x08109194]
[0x08109abf]
[0x0819d78c]
[0x0819ddd2]
[0x0819dfae]
[0x083d7d7e]
[0xb7ad9050]
[0x0804ca61]
********************
ERROR: The current video card / driver combination does not support the necessary features: GL_EXT_texture3D GL_ARB_texture_rectangle or GL_EXT_texture_rectangle GL_ARB_occlusion_query GL_ARB_vertex_program GL_ARB_fragment_program
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Error during initialization
```

I have a feeling I am going to get this when I try and run the other games I want to install.

I can see this is to do with opengl, but I have no idea where to start with this.

Can anybody help?

Thanks!

---

### Post by jan quark on 2008-02-18
make sure your graphic card has the drivers it needs
and that it supports the features required by the game

run these commands an post the output please
```

lspci
```

```
sudo lshw 
```
```

glxgears -info
```

---

### Post by msjones on 2008-02-18
Thanks for the reply. Will post the results as soon as I get home!

---

### Post by msjones on 2008-02-18
Hi,

Right here are my outputs...

lspci:
> 00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation Unknown device 07cb (rev a2)
00:01.0 RAM memory: nVidia Corporation Unknown device 07cd (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 07ce (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 07cf (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 07d0 (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 07d1 (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 07d2 (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 07d3 (rev a1)
00:02.0 RAM memory: nVidia Corporation Unknown device 07d6 (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 07fe (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 056a (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation Unknown device 07fc (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation Unknown device 07dc (rev a2)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
02:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)

sudo lshw:
> mj-tuxbox                 
    description: Desktop Computer
    product: GA-73PVM-S2H
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=30303141-3444-3543-3146-3937FFFFFFFF
  *-core
       description: Motherboard
       product: GA-73PVM-S2H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       serial: Mon Dec 03 11:32:07 2007
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3 (11/07/2007)
          size: 128KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2140  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 775
          size: 2GHz
          capacity: 3200MHz
          width: 64 bits
          clock: 250MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 64KB
             capacity: 64KB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 1MB
             capacity: 1MB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 2GB
        *-bank:0
             description: DIMM 667 MHz (1.5 ns)
             physical id: 0
             slot: A0
             size: 1GB
             width: 3584 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             physical id: 1
             slot: A1
             size: 1GB
             width: 1024 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: nVidia Corporation
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             capabilities: bus_master
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:5 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:6 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.5
             bus info: pci@0000:00:01.5
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:7 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:8 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-memory:9 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:10 UNCLAIMED
             description: RAM memory
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 3.4
             bus info: pci@0000:00:03.4
             version: a1
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 4.1
             bus info: pci@0000:00:04.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
        *-ide:0
             description: IDE interface
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=AMD_IDE latency=0 maxlatency=1 mingnt=3 module=amd74xx
        *-multimedia
             description: Audio device
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:01:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
        *-pci:1
             description: PCI bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV535 [Radeon X1650 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV535 [Radeon X1650 Series]
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 9e
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: c
             bus info: pci@0000:00:0c.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:3
             description: PCI bridge
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:1
             description: IDE interface
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             logical name: scsi0
             logical name: scsi1
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
           *-disk
                description: SCSI Disk
                product: ST3250820AS
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.AD
                serial: 9QE6RMQ8
                size: 232GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 46GB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux swap / Solaris partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 5247MB
                   capabilities: primary nofs
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 181GB
                   capabilities: primary
           *-cdrom
                description: DVD writer
                product: DVD+-RW GSA-H73N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: B103
                serial: [HL-DT-STDVD+-RW GSA-H73NB10307/06/27 7U02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-network
             description: Ethernet interface
             product: nVidia Corporation
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth19
             version: a2
             serial: 00:00:6c:d0:10:39
             size: 100MB/s
             capacity: 1GB/s
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 duplex=full ip=10.0.10.10 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s

glxgears -info:
> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
GL_RENDERER   = Radeon X1650 Series
GL_VERSION    = 1.2 (2.0.6473 (8.37.6))
GL_VENDOR     = ATI Technologies Inc.
GL_EXTENSIONS = GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 
59078 frames in 5.0 seconds = 11809.714 FPS
58134 frames in 5.0 seconds = 11621.923 FPS
59654 frames in 5.0 seconds = 11918.322 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":1.0"
      after 457136 requests (456494 known processed) with 0 events remaining.


I am using the restricted drivers that came with ubuntu 7.10. Everything like compiz etc is wokring fine without problems. I just want be able to play linux games like doom3 UT etc.

Thanks again!

---

### Post by Kubunteando on 2008-07-10
Clearly there is an issue with the drivers.

They are not working properly.

Did the drivers install correctly?

What is the output of "glxinfo | grep -i render
"?

There you can see what are the current drivers for OpenGL

---

### Post by anliveyak on 2009-02-17
thank you for the reply...
this is he otput:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
as far as i can tell everything installed ok
again thank you for the help

---

### Post by InFeh on 2009-02-18
It would seem you should first disable the driver, reboot, and re-enable it.
A reinstall might be useful between the disable and the re-enable, but I can't remember its package-name as I've somehow gotten stuck with ATI. :(

---

### Post by Bölvaður on 2009-02-18
perhaps if you are up for it, you may go to 8.04 or 8.10 or even 9.04 if you are brave enough for alpha :)
I would assume that the drivers in the 7.10 repos might not be totally up to date

---

### Post by R33D3M33R on 2009-02-20
If everything else fails, try to use the binary driver from nvidia. Download it from the nvidia website, shutdown xserver and install it.
Post if you need more help.

---

