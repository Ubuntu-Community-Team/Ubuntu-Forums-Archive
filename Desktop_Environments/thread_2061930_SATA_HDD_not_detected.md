---
title: "SATA HDD not detected"
date: 2012-09-23
forum: Desktop Environments
---

### Post by Kapsonas on 2012-09-23
Hi,

I have worked with Ubuntu for few years already and installed Ubuntu and other distros to a lot of PCs, but this type of problem I could not resolve by my self.

I have Desktop PC with SATA HDD, where I have installed Win7, no problem, everything works. I wanted next to it install Ubuntu 12.04, however when Ubuntu from live CD or USB boots it does not see the hard disk. I can see only the USB drive from which I boot. Gparted and Fdisk, don't see it. I reboot the system, the Win7 boots without any problem.

I have tried a lot of things, but non of them seems to be working:
  In bios I have changed Sata Mode to AHCI, SATA mode and RAID mode - no effect (while Win boots on AHCI and SATA  mode).
  Bios detects HDD and I an choose booting device. The HDD is not shown in Standart CMOS setup page, where only PATA disks are shown.
   Tried different SATA connectors to motherboard (there are 5 of them) - no result.
   My HDD is 2TB, which is not detected, but I also tried with old SATA 40Gb hard disk, the result is the same, the HDD is not detected.
   One good thing is that I know, because tried, that Ubuntu boots and can be installed from PATA HDD, but I would like to install it to SATA. As I don't have the very old PATA disk.
    I wanted to update the BIOS, but there is no newer, spent a lot of time looking for it. Motherboard - Packard Bell MCP78PVM-PM, BIOS released 05/01/2008, Computer model: Packard Bell Imedia 8841.
    "Gparted recovery disc" also does not detect the HDD. Meaning that debian based OS will not detect it. I have a bad feeling that the same will be with any Linux distro.
       Tried 32 and 64 bit Ubuntu, with no success. 

I think here I should ask what Win7 can do better in SATA HDD detection than Linux and how can I add this to Linux (without recompiling kernel).

Please suggest what more could be done. I don't want to be stuck just with Win7, it's so not interesting.

---

### Post by Kapsonas on 2012-09-25
Someone asked for what gives LSHW, here it is:

ubuntu                    
    description: Desktop Computer
    product: IMEDIA 8841 ()
    vendor: Packard Bell BV
    version: PB80132991
    serial: 820004100335
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=3 uuid=60897581-4C17-DD11-A5C9-AFAE7343A631
  *-core
       description: Motherboard
       vendor: Packard Bell BV
       physical id: 0
       version: 1.0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: PBCBR00.P23
          date: 05/01/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Phenom(tm) 8450 Triple-Core Processor
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 3
          bus info: cpu@0
          version: 15.2.3
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1050MHz
          capacity: 2100MHz
          width: 64 bits
          clock: 200MHz
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs npt lbrv svm_lock cpufreq
          configuration: cores=3 enabledcores=3
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 384KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1536KiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified
     *-memory:0
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: 64T128020EU3SB2
             vendor: Qimonda
             physical id: 0
             serial: 15970606
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: 64T128020EU3SB2
             vendor: Qimonda
             physical id: 1
             serial: 10970606
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: 64T128020HU3.7A
             vendor: Qimonda
             physical id: 2
             serial: 16811206
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 266 MHz (3.8 ns)
             product: 64T128020HU3.7A
             vendor: Qimonda
             physical id: 3
             serial: 10811206
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.2.3
          size: 2100MHz
          capacity: 2100MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-cpu:2
          physical id: 5
          bus info: cpu@2
          version: 15.2.3
          size: 1050MHz
          capacity: 1050MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: NVIDIA Corporation
          physical id: a
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP78S [GeForce 8200] LPC Bridge
          vendor: NVIDIA Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:2f00(size=256)
     *-serial
          description: SMBus
          product: MCP78S [GeForce 8200] SMBus
          vendor: NVIDIA Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:2900(size=64) ioport:2d00(size=64) ioport:2e00(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP78S [GeForce 8200] Co-Processor
          vendor: NVIDIA Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:fbf80000-fbffffff
     *-memory:3 UNCLAIMED
          description: RAM memory
          product: MCP78S [GeForce 8200] Memory Controller
          vendor: NVIDIA Corporation
          physical id: 1.4
          bus info: pci@0000:00:01.4
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:fbf7f000-fbf7ffff
     *-usb:1
          description: USB controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fbf7ec00-fbf7ecff
     *-usb:2
          description: USB controller
          product: MCP78S [GeForce 8200] OHCI USB 1.1 Controller
          vendor: NVIDIA Corporation
          physical id: b
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fbf7d000-fbf7dfff
     *-usb:3
          description: USB controller
          product: MCP78S [GeForce 8200] EHCI USB 2.0 Controller
          vendor: NVIDIA Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:fbf7e800-fbf7e8ff
     *-ide
          description: IDE interface
          product: MCP78S [GeForce 8200] IDE
          vendor: NVIDIA Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          logical name: scsi7
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-cdrom
             description: DVD writer
             product: DVD Writer 640c
             vendor: HP
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: ES04
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-multimedia
          description: Audio device
          product: MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio
          vendor: NVIDIA Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
          resources: irq:22 memory:fbf78000-fbf7bfff
     *-pci:0
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht subtractive_decode bus_master cap_list
     *-storage
          description: SATA controller
          product: MCP78S [GeForce 8200] AHCI Controller
          vendor: NVIDIA Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: storage pm msi ahci_1.0 bus_master cap_list
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:40 ioport:c480(size=8) ioport:c400(size=4) ioport:c080(size=8) ioport:c000(size=4) ioport:bc00(size=16) memory:fbf76000-fbf77fff
     *-pci:1
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:19 ioport:d000(size=4096) memory:fc000000-feafffff ioport:d4000000(size=201326592)
        *-display
             description: VGA compatible controller
             product: GF104 [GeForce GTX 460]
             vendor: NVIDIA Corporation
             physical id: 0
             bus info: pci@0000:02:00.0
             version: a1
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
             configuration: driver=nouveau latency=0
             resources: irq:19 memory:fc000000-fdffffff memory:d8000000-dfffffff memory:d4000000-d7ffffff ioport:dc00(size=128) memory:fea80000-feafffff
        *-multimedia
             description: Audio device
             product: GF104 High Definition Audio Controller
             vendor: NVIDIA Corporation
             physical id: 0.1
             bus info: pci@0000:02:00.1
             version: a1
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:16 memory:fea7c000-fea7ffff
     *-pci:2
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Express Bridge
          vendor: NVIDIA Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:18
     *-pci:3
          description: PCI bridge
          product: MCP78S [GeForce 8200] PCI Bridge
          vendor: NVIDIA Corporation
          physical id: 13
          bus info: pci@0000:00:13.0
          version: a1
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:17 ioport:e000(size=4096) memory:feb00000-febfffff
        *-network
             description: Ethernet interface
             product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 0
             bus info: pci@0000:04:00.0
             logical name: eth0
             version: 01
             serial: 00:1e:90:32:04:0a
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.139 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
             resources: irq:41 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff
     *-pci:4
          description: Host bridge
          product: Family 10h Processor HyperTransport Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Family 10h Processor Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Family 10h Processor DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Family 10h Processor Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Family 10h Processor Link Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: c
          bus info: usb@2:1
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sda
             size: 3935MiB (4126MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0217934c
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sda1
                logical name: /cdrom
                version: FAT16
                serial: 5c73-f628
                size: 3934MiB
                capacity: 3934MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted

---

### Post by Kapsonas on 2012-09-25
The modprobe sata_nv

ubuntu@ubuntu:~$ sudo modprobe sata_nv
ubuntu@ubuntu:~$ dmesg| tail
[   67.581116] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input16
[   67.583276] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1/input17
[   67.868533] init: plymouth-stop pre-start process (2838) terminated with status 1
[   73.374017] [drm] nouveau 0000:02:00.0: PMFB0_SUBP0: 0x037f0040
[   73.374024] [drm] nouveau 0000:02:00.0: PMFB0_SUBP1: 0x037f0000
[   73.374030] [drm] nouveau 0000:02:00.0: PMFB1_SUBP0: 0x037f0000
[   73.374035] [drm] nouveau 0000:02:00.0: PMFB1_SUBP1: 0x037f0040
[   73.374039] [drm] nouveau 0000:02:00.0: PMFB2_SUBP0: 0x037f0040
[   73.374044] [drm] nouveau 0000:02:00.0: PMFB2_SUBP1: 0x037f0000
[   77.432024] eth0: no IPv6 routers present

---

### Post by gordintoronto on 2012-09-25
Set the SATA mode to AHCI. Do you actually power down the computer between tries?

The SATA Controller does not have a logical name assigned, which might point to where the problem lies. Support for that controller has been in the kernel for several years, so it should "just work." Sorry, I know that doesn't help.

---

### Post by kagebunjutsu on 2012-10-01
i got the same problem and its driving me nuts :(.. dos utility/hardisk utility can see the disk but ubuntu doesnt :( i hope someone out there already experience this problem and have a solution to this one :(.. i will try to post my logs, im currently at the office right now

---

