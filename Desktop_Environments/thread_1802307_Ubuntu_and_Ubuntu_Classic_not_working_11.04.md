---
title: "Ubuntu and Ubuntu Classic not working 11.04"
date: 2011-07-11
forum: Desktop Environments
---

### Post by salgala2000 on 2011-07-11
Hello,

I recently installed Ubuntu 11.04 on my Dell Desktop. When I try to log into Ubuntu or Ubuntu Classic, there are lots of pixel glitches. Any window that I open stays open for a fraction of a second before becoming "invisible" again. In Ubuntu Classic (No Effects) and Ubuntu (Safe Mode) the windows stay open and the computer is usable, but there are still pixel glitches on the toolbars and other places. I would like to know what I can do to run Ubuntu in the normal or Classic version without the windows only being visible for a fraction of a second.
Thank you :D

I can provide screenshots if necessary.

TL;DR: Ubuntu Classic and Ubuntu are unusable because of pixel glitches and windows only being visible for fractions of a second.

---

### Post by wildmanne39 on 2011-07-11
> **salgala2000 said:**
> Hello,

I recently installed Ubuntu 11.04 on my Dell Desktop. When I try to log into Ubuntu or Ubuntu Classic, there are lots of pixel glitches. Any window that I open stays open for a fraction of a second before becoming "invisible" again. In Ubuntu Classic (No Effects) and Ubuntu (Safe Mode) the windows stay open and the computer is usable, but there are still pixel glitches on the toolbars and other places. I would like to know what I can do to run Ubuntu in the normal or Classic version without the windows only being visible for a fraction of a second.
Thank you :D

I can provide screenshots if necessary.

TL;DR: Ubuntu Classic and Ubuntu are unusable because of pixel glitches and windows only being visible for fractions of a second.Hi run these commands in a terminal
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
```
sudo lshw
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by salgala2000 on 2011-07-12
Thank you very much! The information is rather long, I'm not sure if you meant all of it, but I will post it just in case.

```
salvador@ubuntu:~$ lspci | grep VGA
 00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 salvador@ubuntu:~$ /usr/lib/nux/unity_support_test -p
 OpenGL vendor string:   Tungsten Graphics, Inc
 OpenGL renderer string: Mesa DRI Intel(R) 865G GEM 20100330 DEVELOPMENT x86/MMX/SSE2
 OpenGL version string:  1.3 Mesa 7.10.2
 
 Not software rendered:    yes
 Not blacklisted:          yes
 GLX fbconfig:             yes
 GLX texture from pixmap:  yes
 GL npot or rect textures: yes
 GL vertex program:        yes
 GL fragment program:      no
 GL vertex buffer object:  yes
 GL framebuffer object:    yes
 GL version is 1.4+:       no
 
 Unity supported:          no
 salvador@ubuntu:~$ sudo lshw
 [sudo] password for salvador: 
 ubuntu                    
     description: Mini Tower Computer
     width: 32 bits
     capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
     configuration: administrator_password=enabled boot=normal  chassis=mini-tower cpus=1 power-on_password=enabled  uuid=44454C4C-3800-1032-8052-C6C04F373731
   *-core
        description: Motherboard
        product: 0K8980
        vendor: Winbond Electronics
        physical id: 0
        serial: ..CN7082151FA3BT.
      *-firmware
           description: BIOS
           vendor: Winbond Electronics
           physical id: 0
           version: A02
           date: 11/08/2004
           size: 64KiB
           capacity: 448KiB
           capabilities: pci pnp apm upgrade shadowing escd cdboot  bootselect edd int13floppytoshiba int5printscreen int9keyboard  int14serial int17printer acpi usb ls120boot biosbootspecification  netboot
      *-cpu
           description: CPU
           product: Intel(R) Pentium(R) 4 CPU 2.80GHz
           vendor: Intel Corp.
           physical id: 400
           bus info: cpu@0
           version: 15.4.1
           serial: 0000-0F41-0000-0000-0000-0000
           slot: Microprocessor
           size: 2800MHz
           capacity: 3600MHz
           width: 32 bits
           clock: 533MHz
           capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse  sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid  xtpr
           configuration: id=0
         *-cache:0
              description: L1 cache
              physical id: 700
              size: 8KiB
              capacity: 16KiB
              capabilities: internal write-back data
         *-cache:1
              description: L2 cache
              physical id: 701
              size: 1MiB
              capacity: 1MiB
              capabilities: internal varies unified
      *-memory
           description: System Memory
           physical id: 1000
           slot: System board or motherboard
           size: 512MiB
         *-bank:0
              description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
              physical id: 0
              slot: DIMM_1
              size: 256MiB
              width: 64 bits
              clock: 333MHz (3.0ns)
         *-bank:1
              description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
              physical id: 1
              slot: DIMM_2
              size: 256MiB
              width: 64 bits
              clock: 333MHz (3.0ns)
      *-pci
           description: Host bridge
           product: 82865G/PE/P DRAM Controller/Host-Hub Interface
           vendor: Intel Corporation
           physical id: 100
           bus info: pci@0000:00:00.0
           version: 02
           width: 32 bits
           clock: 33MHz
           configuration: driver=agpgart-intel
           resources: irq:0 memory:f0000000-f7ffffff
         *-display
              description: VGA compatible controller
              product: 82865G Integrated Graphics Controller
              vendor: Intel Corporation
              physical id: 2
              bus info: pci@0000:00:02.0
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: pm vga_controller bus_master cap_list rom
              configuration: driver=i915 latency=0
              resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff ioport:ed98(size=:cool:
         *-generic UNCLAIMED
              description: System peripheral
              product: 82865G/PE/P Processor to I/O Memory Interface
              vendor: Intel Corporation
              physical id: 6
              bus info: pci@0000:00:06.0
              version: 02
              width: 32 bits
              clock: 33MHz
              configuration: latency=0
              resources: memory:fecf0000-fecf0fff
         *-usb:0
              description: USB Controller
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
              vendor: Intel Corporation
              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master
              configuration: driver=uhci_hcd latency=0
              resources: irq:16 ioport:ff80(size=32)
         *-usb:1
              description: USB Controller
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
              vendor: Intel Corporation
              physical id: 1d.1
              bus info: pci@0000:00:1d.1
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master
              configuration: driver=uhci_hcd latency=0
              resources: irq:19 ioport:ff60(size=32)
         *-usb:2
              description: USB Controller
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
              vendor: Intel Corporation
              physical id: 1d.3
              bus info: pci@0000:00:1d.3
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: uhci bus_master
              configuration: driver=uhci_hcd latency=0
              resources: irq:16 ioport:ff20(size=32)
         *-usb:3
              description: USB Controller
              product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
              vendor: Intel Corporation
              physical id: 1d.7
              bus info: pci@0000:00:1d.7
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: pm debug ehci bus_master cap_list
              configuration: driver=ehci_hcd latency=0
              resources: irq:23 memory:ffa80800-ffa80bff
         *-pci
              description: PCI bridge
              product: 82801 PCI Bridge
              vendor: Intel Corporation
              physical id: 1e
              bus info: pci@0000:00:1e.0
              version: c2
              width: 32 bits
              clock: 33MHz
              capabilities: pci normal_decode bus_master
              resources: ioport:d000(size=4096) memory:fea00000-feafffff
            *-communication UNCLAIMED
                 description: Communication controller
                 product: HSF 56k Data/Fax Modem
                 vendor: Conexant Systems, Inc.
                 physical id: 1
                 bus info: pci@0000:01:01.0
                 version: 00
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm bus_master cap_list
                 configuration: latency=64
                 resources: memory:feaf0000-feafffff ioport:df38(size=:cool:
            *-network
                 description: Ethernet interface
                 product: 82562EZ 10/100 Ethernet Controller
                 vendor: Intel Corporation
                 physical id: 8
                 bus info: pci@0000:01:08.0
                 logical name: eth0
                 version: 02
                 serial: 00:13:20:01:63:ad
                 size: 100Mbit/s
                 capacity: 100Mbit/s
                 width: 32 bits
                 clock: 33MHz
                 capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes  driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A  ip=192.168.1.117 latency=64 link=yes maxlatency=56 mingnt=8  multicast=yes port=MII speed=100Mbit/s
                 resources: irq:20 memory:feaef000-feaeffff ioport:df40(size=64)
         *-isa
              description: ISA bridge
              product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
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
              product: 82801EB/ER (ICH5/ICH5R) IDE Controller
              vendor: Intel Corporation
              physical id: 1f.1
              bus info: pci@0000:00:1f.1
              logical name: scsi0
              logical name: scsi1
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: ide bus_master emulated
              configuration: driver=ata_piix latency=0
              resources: irq:18 ioport:1f0(size=:cool: ioport:3f6 ioport:170(size=:cool: ioport:376 ioport:ffa0(size=16) memory:feb7fc00-feb7ffff
            *-disk
                 description: ATA Disk
                 product: WDC WD800BB-75JH
                 vendor: Western Digital
                 physical id: 0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/sda
                 version: 06.0
                 serial: WD-WMAM99675404
                 size: 74GiB (80GB)
                 capabilities: partitioned partitioned:dos
                 configuration: ansiversion=5 signature=d0f4738c
               *-volume:0
                    description: Windows FAT volume
                    vendor: Winbond Electronics
                    physical id: 1
                    bus info: scsi@0:0.0.0,1
                    logical name: /dev/sda1
                    version: FAT16
                    serial: 07d5-0805
                    size: 31MiB
                    capacity: 31MiB
                    capabilities: primary fat initialized
                    configuration: FATs=2 filesystem=fat label=DellUtility
               *-volume:1
                    description: Windows NTFS volume
                    physical id: 2
                    bus info: scsi@0:0.0.0,2
                    logical name: /dev/sda2
                    logical name: /host
                    version: 3.1
                    serial: ce18ca23-ea02-6f4e-8095-63032ba32f3e
                    size: 71GiB
                    capacity: 71GiB
                    capabilities: primary bootable ntfs initialized
                    configuration: clustersize=4096 created=2005-08-05  09:34:08 filesystem=ntfs mount.fstype=fuseblk  mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096  state=mounted
               *-volume:2
                    description: Windows FAT volume
                    vendor: MSWIN4.1
                    physical id: 3
                    bus info: scsi@0:0.0.0,3
                    logical name: /dev/sda3
                    version: FAT32
                    serial: 0000-0000
                    size: 2786MiB
                    capacity: 2816MiB
                    capabilities: primary fat initialized
                    configuration: FATs=2 filesystem=fat label=DellRestore
            *-cdrom
                 description: DVD reader
                 product: RW/DVD GCC-4481B
                 vendor: HL-DT-ST
                 physical id: 1
                 bus info: scsi@1:0.0.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/scd0
                 logical name: /dev/sr0
                 version: E106
                 capabilities: removable audio cd-r cd-rw dvd
                 configuration: ansiversion=5 status=nodisc
         *-serial UNCLAIMED
              description: SMBus
              product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
              vendor: Intel Corporation
              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 02
              width: 32 bits
              clock: 33MHz
              configuration: latency=0
              resources: ioport:eda0(size=32)
         *-multimedia
              description: Multimedia audio controller
              product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
              vendor: Intel Corporation
              physical id: 1f.5
              bus info: pci@0000:00:1f.5
              version: 02
              width: 32 bits
              clock: 33MHz
              capabilities: pm bus_master cap_list
              configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:ee00(size=256) ioport:edc0(size=64) memory
```

---

### Post by mikewhatever on 2011-07-12
The Ubuntu and Ubuntu Classic options are really Unity and Compiz. Since you have an old Intel graphics both options won't work. Use the one with no effects.

---

### Post by salgala2000 on 2011-07-12
Ah, okay. There are still a fair number of stuck pixels and things like that in the No Effects mode, is there a solution for these?

---

### Post by mikewhatever on 2011-07-12
Not sure really. What do you mean by 'stuck pixels'?

---

### Post by salgala2000 on 2011-07-12
There was a Ubuntu update and the problems were fixed. Thank you for your help!:D

---

### Post by wildmanne39 on 2011-07-12
Hi, your welcome would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

