---
title: "Screen goes black when I run &quot;sudo lshw&quot;"
date: 2016-09-07
forum: Desktop Environments
---

### Post by watchpocket on 2016-09-07
If I run the [COLOR=#0000ff]***lshw***[/COLOR] command as user, I see what you'd expect to see:
```

rjbox
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 7981MiB
     *-cpu
          product: Intel(R) Core(TM)2 Quad CPU    Q9650  @ 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 2997MHz
          capacity: 2997MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:e0000000-ee0fffff
           *-display
                description: VGA compatible controller
                product: GF106 [GeForce GTS 450]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:50 memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:ee000000-ee07ffff
           *-multimedia
                description: Audio device
                product: GF106 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:ee080000-ee083fff
        *-network
             description: Ethernet interface
             product: 82567LF-2 Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 00
             serial: 00:27:0e:01:b2:89
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k duplex=full firmware=1.8-5 ip=192.168.1.19 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:48 memory:ee300000-ee31ffff memory:ee324000-ee324fff ioport:f100(size=32)
        *-usb:0
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:f0e0(size=32)
        *-usb:1
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:f0c0(size=32)
        *-usb:2
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f0a0(size=32)
        *-usb:3
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:ee325c00-ee325fff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:51 memory:ee320000-ee323fff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:ee400000-ee5fffff ioport:ee600000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:3000(size=4096) memory:ee200000-ee2fffff ioport:ee800000(size=2097152)
           *-usb
                description: USB controller
                product: uPD720202 USB 3.0 Host Controller
                vendor: Renesas Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:17 memory:ee200000-ee201fff
        *-usb:4
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:f080(size=32)
        *-usb:5
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:f060(size=32)
        *-usb:6
             description: USB controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:f040(size=32)
        *-usb:7
             description: USB controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ee325800-ee325bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:ee100000-ee1fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=24 mingnt=12
                resources: irq:19 memory:ee110000-ee110fff
           *-network
                description: Wireless interface
                product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
                vendor: Qualcomm Atheros
                physical id: 3
                bus info: pci@0000:04:03.0
                logical name: wlan0
                version: 01
                serial: 00:24:01:11:e5:e1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=3.13.0-95-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:ee100000-ee10ffff
        *-isa
             description: ISA bridge
             product: 82801JIR (ICH10R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 82801JI (ICH10 Family) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:49 ioport:f150(size=8) ioport:f140(size=4) ioport:f130(size=8) ioport:f120(size=4) ioport:f020(size=32) memory:ee325000-ee3257ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:ee326000-ee3260ff ioport:f000(size=32)


```

But if I run [COLOR=#0000ff]***sudo lshw***[/COLOR], and then count to five, both my monitors go black, with a blinking white line-cursor at the upper left of the main monitor.

My only escape from this black screen (as far as I know, though maybe there's a better way) is to press the* reset* button on the front of my computer.

This is on Ubuntu-MATE Trusty 14.04.5 LTS.

Would anyone know why this be happening, & how I can fix it?  

Thanks.

---

### Post by watchpocket on 2016-09-08
This*** may*** be a bug, as it's very similar to this (except I don't get the "smashed stack" error message): [https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/1414476](https://bugs.launchpad.net/ubuntu/+source/lshw/+bug/1414476)

---

### Post by mörgæs on 2016-09-08
The bug report to which you linked points to 1427436, in which the status is 'Fix released'. 

This fix alone is probably not enough for you to consider a fresh install of 16.04, but when you do some day then you can look forward to having one bug less.

---

### Post by watchpocket on 2016-09-08
I've got a 16.04 install on my other drive, so yes, it's very good to know the *sudo lshw* problem won't happen over there.

---

### Post by mörgæs on 2016-09-09
If this solves the problem please mark the thread so.

---

