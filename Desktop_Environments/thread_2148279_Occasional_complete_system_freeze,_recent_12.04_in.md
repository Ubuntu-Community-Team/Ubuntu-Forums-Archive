---
title: "Occasional complete system freeze, recent 12.04 install"
date: 2013-05-24
forum: Desktop Environments
---

### Post by pmantis on 2013-05-24
SHORT DESCRIPTION:
Random, every few day lockups. Screen stays on, needs hardware reset to come back. Need help diagnosing.


LONG (in parts):
HISTORY:
I have a desktop computer that I've been using for a number of months. I originally installed 12.04, then over the course its life so far, I upgraded to 12.10, later installed a video card (Radeon HD 7970) which forced me to flash the BIOS (EFI) on the motherboard to get the system to POST, then later still, upgraded to 13.04 the weekend after it came out. Immediately upon upgrading to 13.04, the system booted to a graphical screen that complained about running in low graphics mode and suggested some options. This turned out to be the death of my system since I never figured out how to recover. I couldn't uninstall the Radeon drivers (uninstaller crashed), and couldn't install it again (forgot why). The X11 backup config didn't work and my forum searches didn't give me any answers. Since I'm self-employed and this is my business computer, I had to get it working. The next weekend, I accepted the upgrade as a failure and wiped the drives to install 12.04, since 12.10 doesn't have an alternate DVD to install RAID, and my manually installed RAID on a 12.10 system failed. In hindsight, I think this was because of trying to use the newer EFI supported partitioning in combination with MD, but I digress...

CURRENT:
About 2-2.5 weeks ago, I installed a fresh copy of 12.04 after having to DBAN the drives to revert to the classic (MBR) partitioning scheme. The install went smoothly and I proceeded to add all the packages I wanted, and restored my home directory from backup, etc. Ever since my adventure into the EFI world with partitioning, and the latest reinstall, the system has been less stable.

SYSTEM INFO:
Gigabyte motherboard, Intel CPU, dual Samsung F3 1TB drives in RAID1, SATA DVD writer, TV capture card (for occasional MyTV use), dual monitors
System is usually on 24/7 in my home office. Kids/animals do not go in here without me, door kept shut when I'm not home.

PROBLEM SYMPTOMS:
Occasional system lockup (every few days). This usually occurs while I'm using the computer, and usually while moving the mouse. I simply notice the mouse stops moving, then I wiggle it, wait, hope... nope, locked. I've walked away for a few minutes to shower, but still locked when I come back. I've tried Ctrl-Alt-F1, no screen change. I've tried to ping the computer on the network (no response to ICMP). I've tried Ctrl-Alt-SysReq-s & b, no disk activity nor reboot respectively. Lastly, when I finally press the reset button (press and release) the system DOES NOT RESET! This is what surprised me the most. This looks like a complete hardware level lockup. However, there must be a watchdog of some sort, since about 10 seconds after pressing the reset button, the system completely powers itself off, delays 3 seconds (about) then powers on to boot. Again, this *IS* the reset button, not the power button, and I only press and release once.

I do not recall having any major issues until my 13.04 upgrade and forced reinstall attempts.


REQUEST:
Please suggest further diagnostic steps to help narrow down the cause. 

Thank you!




COMPLETE HARDWARE INFO (Less serial numbers:)
```
~$ sudo lshw | grep -v serial
my-desktop          
    description: Desktop Computer
    product: To be filled by O.E.M. (To be filled by O.E.M.)
    vendor: Gigabyte Technology Co., Ltd.
    version: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=90022B03-3404-3705-AC06-CC0700080009
  *-core
       description: Motherboard
       product: Z77X-UD3H
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F18
          date: 10/24/2012
          size: 64KiB
          capacity: 8128KiB
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: CPU Internal L1
          size: 128KiB
          capacity: 128KiB
          capabilities: internal write-through
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through instruction
     *-cache:2
          description: L3 cache
          physical id: 6
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CMZ16GX3M2A1866C9
             vendor: AMI
             physical id: 0
             slot: ChannelB-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: CMZ16GX3M2A1866C9
             vendor: AMI
             physical id: 1
             slot: ChannelA-DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 2
             slot: ChannelB-DIMM0
        *-bank:3
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             slot: ChannelA-DIMM0
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 43
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          slot: Intel(R) Core(TM) i5-3470 CPU @ 3.20GHz
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=1
     *-pci
          description: Host bridge
          product: Ivy Bridge DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Ivy Bridge Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:47 memory:f7000000-f73fffff memory:e0000000-efffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: Panther Point USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:44 memory:f7700000-f770ffff
        *-communication
             description: Communication controller
             product: Panther Point MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:46 memory:f771a000-f771a00f
        *-usb:1
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f7718000-f77183ff
        *-multimedia
             description: Audio device
             product: Panther Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:48 memory:f7710000-f7713fff
        *-pci:0
             description: PCI bridge
             product: Panther Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:1
             description: PCI bridge
             product: Panther Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:f7600000-f76fffff
           *-usb
                description: USB controller
                product: VIA Technologies, Inc.
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:45 memory:f7600000-f7600fff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm subtractive_decode bus_master cap_list
             resources: memory:f3000000-f6ffffff
           *-pci
                description: PCI bridge
                product: 82801 PCI Bridge
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 41
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: memory:f3000000-f6ffffff
              *-multimedia:0
                   description: Multimedia video controller
                   product: CX23880/1/2/3 PCI Video and Audio Decoder
                   vendor: Conexant Systems, Inc.
                   physical id: 0
                   bus info: pci@0000:04:00.0
                   version: 05
                   width: 32 bits
                   clock: 33MHz
                   capabilities: vpd pm bus_master cap_list
                   configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
                   resources: irq:17 memory:f6000000-f6ffffff
              *-multimedia:1
                   description: Multimedia controller
                   product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                   vendor: Conexant Systems, Inc.
                   physical id: 0.1
                   bus info: pci@0000:04:00.1
                   version: 05
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=cx88_audio latency=32 maxlatency=255 mingnt=4
                   resources: irq:17 memory:f5000000-f5ffffff
              *-multimedia:2
                   description: Multimedia controller
                   product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
                   vendor: Conexant Systems, Inc.
                   physical id: 0.2
                   bus info: pci@0000:04:00.2
                   version: 05
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: driver=cx88-mpeg driver manager latency=32 maxlatency=88 mingnt=6
                   resources: irq:17 memory:f4000000-f4ffffff
              *-multimedia:3 UNCLAIMED
                   description: Multimedia controller
                   product: CX23880/1/2/3 PCI Video and Audio Decoder [IR Port]
                   vendor: Conexant Systems, Inc.
                   physical id: 0.4
                   bus info: pci@0000:04:00.4
                   version: 05
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm bus_master cap_list
                   configuration: latency=32 maxlatency=255 mingnt=6
                   resources: memory:f3000000-f3ffffff
        *-pci:3
             description: PCI bridge
             product: Panther Point PCI Express Root Port 7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:e000(size=4096) memory:f7500000-f75fffff
           *-network
                description: Ethernet interface
                product: AR8151 v2.0 Gigabit Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: c0
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:49 memory:f7500000-f753ffff ioport:e000(size=128)
        *-pci:4
             description: PCI bridge
             product: Panther Point PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:f7400000-f74fffff
           *-storage
                description: SATA controller
                product: 88SE9172 SATA 6Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:43 ioport:d040(size=8) ioport:d030(size=4) ioport:d020(size=8) ioport:d010(size=4) ioport:d000(size=16) memory:f7410000-f74101ff memory:f7400000-f740ffff
        *-usb:2
             description: USB controller
             product: Panther Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f7717000-f77173ff
        *-isa
             description: ISA bridge
             product: Panther Point LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Panther Point 6 port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             logical name: scsi4
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7716000-f77167ff
           *-disk:0
                description: ATA Disk
                product: SAMSUNG HD103UJ
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 1AA0
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0003d9bc
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 296MiB
                   capabilities: primary multi
              *-volume:1
                   description: Linux raid autodetect partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 63GiB
                   capabilities: primary multi
              *-volume:2
                   description: Linux raid autodetect partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 867GiB
                   capabilities: primary multi
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD103SJ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 1AJ1
                size: 931GiB (1TB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b7b88
              *-volume:0
                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   capacity: 296MiB
                   capabilities: primary bootable multi
              *-volume:1
                   description: Linux raid autodetect partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   capacity: 63GiB
                   capabilities: primary multi
              *-volume:2
                   description: Linux raid autodetect partition
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   capacity: 867GiB
                   capabilities: primary multi
           *-cdrom
                description: DVD-RAM writer
                product: DRW-24B1ST   c
                vendor: ASUS
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/sr0
                version: 1.05
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
             description: SMBus
             product: Panther Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7715000-f77150ff ioport:f040(size=32)
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       capacity: 32768mWh
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@5:1.3
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-43-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn


```

---

