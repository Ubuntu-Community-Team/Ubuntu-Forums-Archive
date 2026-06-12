---
title: "X crashing randomly in lubuntu"
date: 2016-03-28
forum: Desktop Environments
---

### Post by xavier16 on 2016-03-28
I'm having a problem with the X session crashing randomly in lubuntu. I can't reproduce this on demand, but about once a day the screen goes completely black. When this happens, if I press keys on the keyboard it displays keyboard output. If I press ctrl-alt-f1 I can get into a text based console.

I have looked through the logs in /var/log but haven't been able to find the cause. Are there more logs I need to look through? Any ideas on how to troubleshoot/fix this? Below are the specs. Thanks!

*-lubuntu 14.04.1 64-bit LTS*
*-OpenBox 3.5.2*
*-LXDE*

---

### Post by mörgæs on 2016-03-29
Hi, welcome to the fora.

We need to know more of the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by xavier16 on 2016-03-29
> **mörgæs said:**
> Hi, welcome to the fora.

We need to know more of the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Here's the output:


```
computer
    description: Notebook
    product: HP EliteBook Folio 9470m (E1Y37UT#ABA)
    vendor: Hewlett-Packard
    version: A1029D1103
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN G=N L=BUS B=HP S=ELI sku=E1Y37UT#ABA uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 18DF
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 62.19
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: e
          version: 68IBD Ver. F.61
          date: 04/08/2015
          size: 64KiB
          capacity: 5056KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz
          serial: [REMOVED]
          slot: U3E1
          size: 1054MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 4
             slot: Unknown
             size: 3MiB
             capacity: 3MiB
             capabilities: internal write-back unified
     *-cache
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1L16BC4R1-B1GS
             vendor: ADATA
             physical id: 0
             serial: [REMOVED]
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1L16BC4R1-B1GS
             vendor: ADATA
             physical id: 1
             serial: [REMOVED]
             slot: Bottom-Slot 2(under)
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:2000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:27 memory:d0720000-d072ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:31 memory:d0735000-d073500f
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: [REMOVED]
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k firmware=0.15-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:28 memory:d0700000-d071ffff memory:d073b000-d073bfff ioport:2080(size=32)
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d073a000-d073a3ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:33 memory:d0730000-d0733fff
        *-pci:0
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:d0600000-d06fffff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 memory:d0500000-d05fffff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:d0503000-d05030ff memory:d0510000-d051ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d0502000-d05020ff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:d0400000-d04fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6235
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 24
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-34-generic firmware=18.168.6.1 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:32 memory:d0400000-d0401fff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d0739000-d07393ff
        *-isa
             description: ISA bridge
             product: QM77 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:20a8(size=8) ioport:20b4(size=4) ioport:20a0(size=8) ioport:20b0(size=4) ioport:2060(size=32) memory:d0738000-d07387ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0734000-d07340ff ioport:ef80(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HGST HTS725050A7
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: A440
             serial: [REMOVED]
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0000a400
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2016-03-29 00:19:05 mount.fstype=ext2 mount.options=rw,relatime,stripe=4 mounted=2016-03-29 00:19:05 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 465GiB
                capacity: 465GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 465GiB
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: LITEONIT LMS-32L
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 707
             serial: [REMOVED]
             size: 29GiB (32GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=a89c158a
           *-volume
                description: OS/2 hidden C: drive partition
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                capacity: 11GiB
                capabilities: primary hidden
  *-battery
       product: BT04052
       vendor: 33-17
       physical id: 1
       slot: Primary
       capacity: 52540mWh
       configuration: voltage=14.8V
```

---

### Post by mörgæs on 2016-03-30
This might help:
[http://ubuntuforums.org/showthread.php?t=2317790](http://ubuntuforums.org/showthread.php?t=2317790)

---

### Post by xavier16 on 2016-03-30
> **mörgæs said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=2317790](http://ubuntuforums.org/showthread.php?t=2317790)

This seems like a plausible solution to go with 15.10. I'll have to do a fresh install, correct?

---

### Post by xavier16 on 2016-03-30
Okay looks like since I am on LTS I will have to do a fresh install. :cry: I'll let you know how it turns out.

---

### Post by xavier16 on 2016-04-04
I upgraded to 15.10 and it definitely seemed more stable overall and faster. The issue of the screen going completely black didn't come up for about 3-4 days and I was just beginning to rejoice, when it started up again. Can you suggest something in particular to look for in the logs and which logs would be the most relevant for this particular issue?

---

### Post by mörgæs on 2016-04-05
Good to hear. 

I wouldn't begin searching in log files yet. You could try the daily build of 16.04, for example in a live boot, to see if it's even more stable than 15.10.

---

