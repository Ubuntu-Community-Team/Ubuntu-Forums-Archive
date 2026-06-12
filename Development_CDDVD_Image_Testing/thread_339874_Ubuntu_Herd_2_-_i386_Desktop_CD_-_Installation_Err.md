---
title: "Ubuntu Herd 2 - i386 Desktop CD - Installation Error"
date: 2007-01-16
forum: Development CD/DVD Image Testing
---

### Post by ahaslam on 2007-01-16
The i386 herd 2 iso works well as a live cd, but I can't install from it. I launch the installer & successfully go through the first 4 steps, but it crashes & freezes my laptop on the transition to step 5.

Here's a photo of the result:

[ATTACH]23208[/ATTACH]

Hardware info:
```
root@ubuntu:/home/ubuntu# lshw
ubuntu                    
    description: Portable Computer
    product: Packard Bell EasyNote
    vendor: NEC Computers International
    version: PB15M00601
    serial: 251205530230
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=disabled boot=normal chassis=portable power-on_password=disabled uuid=CC626D14-9886-D911-8000-4E45435F4349
  *-core
       description: Motherboard
       vendor: MiTAC
       physical id: 0
       version: 5a
       serial: 0123456789ABCDEF
       slot: Insyde Software SM-BIOS For K8N800
     *-firmware
          description: BIOS
          vendor: Insyde Software
          physical id: 0
          version: R1.06 (11/19/2004)
          size: 84KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot smartbattery netboot
     *-cpu
          description: CPU
          product: Mobile AMD Sempron(tm) Processor 2600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.12.0
          serial: Processor Serial Number
          slot: PGA758
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up lahf_lm ts fid vid ttp cpufreq
        *-cache:0 DISABLED
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KB
             capabilities: burst pipeline-burst internal varies
        *-cache:1 DISABLED
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 128KB
             capacity: 128KB
             capabilities: burst pipeline-burst internal varies
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: DIMM DRAM EDO 1 MHz (1000.0 ns)
             physical id: 0
             slot: DRAM Slot 0
             size: 256MB
             width: 64 bits
             clock: 1MHz (1000.0ns)
        *-bank:1
             description: DIMM DRAM EDO 1 MHz (1000.0 ns)
             physical id: 1
             slot: DRAM Slot 1
             size: 256MB
             width: 64 bits
             clock: 1MHz (1000.0ns)
     *-pci:0
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: b0000000
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=8
          resources: iomemory:b0000000-bfffffff
        *-pci
             description: PCI bridge
             product: VT8237 PCI bridge [K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: S3 Unichrome Pro VGA Adapter
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@01:00.0
                version: 01
                size: 64MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=128 mingnt=2
                resources: iomemory:a4000000-a7ffffff iomemory:e1000000-e1ffffff irq:21
        *-pcmcia
             description: CardBus bridge
             product: CB1410 Cardbus Controller
             vendor: ENE Technology Inc
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
             resources: iomemory:28000000-28000fff irq:16
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22
             resources: ioport:1200-121f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-5-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mass storage device
                   physical id: 2
                   bus info: usb@1:2
                   logical name: scsi2
                   version: 1.00
                   capabilities: usb-2.00 scsi emulated scsi-host
                   configuration: driver=usb-storage maxpower=100mA speed=12.0MB/s
                 *-disk
                      description: SCSI Disk
                      product: Flash Disk
                      vendor: USB
                      physical id: 0.0.0
                      bus info: scsi@2:0.0.0
                      logical name: /dev/sdb
                      version: 2.00
                      size: 124MB
                      capabilities: partitioned partitioned:dos
                      configuration: ansiversion=2
                    *-volume
                         description: FAT16 partition
                         physical id: 1
                         bus info: scsi@2:0.0.0,1
                         logical name: /dev/sdb1
                         capacity: 124MB
                         capabilities: primary bootable
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22
             resources: ioport:1300-131f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-5-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   physical id: 1
                   bus info: usb@2:1
                   version: 4.30
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=100mA speed=1.5MB/s
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=22
             resources: ioport:1700-171f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-5-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: iomemory:f0000000-f00000ff irq:17
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-5-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=6 speed=480.0MB/s
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=pata_via latency=64
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:1100-110f irq:18
           *-disk
                description: SCSI Disk
                product: IC25N040ATMR04-0
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO2O
                serial: MRG2X9KBJ776VH
                size: 37GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 10236MB
                   capabilities: primary bootable
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 17GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 9522MB
                   capabilities: primary
              *-volume:3
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 894MB
                   capabilities: primary nofs
           *-cdrom UNCLAIMED
                description: SCSI CD-ROM
                product: UJ-840D
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                version: 1.00
                capabilities: removable
                configuration: ansiversion=5
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0
             resources: ioport:e000-e0ff irq:20
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Modem latency=0
             resources: ioport:e100-e1ff irq:20
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:40:d0:6d:98:f2
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full ip=192.168.1.3 latency=128 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
             resources: ioport:e200-e2ff iomemory:f0000100-f00001ff irq:19
     *-pci:1
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8M800 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
  *-battery
       product: DR36
       vendor: Duracell
       physical id: 1
       version: 01/06/97
       serial: 0042
       slot: Smart Battery Conn J37
       configuration: voltage=0.0V

```

If you need any more info, let me know. In the mean time I'll install with the alternate CD.

Tony.

---

### Post by pochu on 2007-01-16
Please, report it at Launchpad. And try installing it with the following command:

sudo ubiquity

Thanks
Pochu

---

### Post by Severa on 2007-01-16
I was able to get Herd 2 to install. I had a similar problem as you, once I got past the time zone my screen went all goofy. I hit Ctrl-Alt-F1, then Ctrl-Alt-F7 and it took me right back to where I had left off. Continued installation with no more problems.

Hope this helps!

---

### Post by ahaslam on 2007-01-17
> **Severa said:**
> I was able to get Herd 2 to install. I had a similar problem as you, once I got past the time zone my screen went all goofy. I hit Ctrl-Alt-F1, then Ctrl-Alt-F7 and it took me right back to where I had left off. Continued installation with no more problems.

Hope this helps!

Didn't work, completely locked up. I will follow pochu's suggestion later.

Tony.

---

### Post by viciouslime on 2007-01-17
> **Anthony Haslam said:**
> Didn't work, completely locked up. I will follow pochu's suggestion later.

Tony.

Try pressing ctrl+alt+F1 before you run the installer, then press ctrl+alt+F7 to switch back to the desktop, run the installer, and then press ctral+alt+F1 when it "locks up" and then ctrl+alt+F7 again to get back to the desktop.

Works for me if I do that.

---

### Post by ahaslam on 2007-01-17
> **viciouslime said:**
> Try pressing ctrl+alt+F1 before you run the installer, then press ctrl+alt+F7 to switch back to the desktop, run the installer, and then press ctral+alt+F1 when it "locks up" and then ctrl+alt+F7 again to get back to the desktop.

Works for me if I do that.

Doesn't work for me, freezes completely, responds to nothing (different effects on different hardware I suppose). 

I have submitted the bug on launchpad: [https://bugs.launchpad.net/ubuntu/+bug/80205](https://bugs.launchpad.net/ubuntu/+bug/80205)

I have already installed with the alternate cd, though I will try 'sudo ubiquity' later.

Tony.

---

### Post by ahaslam on 2007-01-17
> **pochu said:**
> 

sudo ubiquity



No different :neutral:

---

### Post by pochu on 2007-01-17
Yes, I knew it wouldn't work, but doesn't it display any output on the terminal? That may help to resolve the problem

Regards
Pochu

---

### Post by ahaslam on 2007-01-17
No, It just launches the installer as expected & freezes at the mentioned point as shown. With it being totally frozen, I can't see/access any output.

Out of curiosity, what is step 5?

---

### Post by pochu on 2007-01-17
Which one is the 4th? ;)

---

### Post by petay on 2007-01-18
i have had the same problem installing

i get to the keyboard language and its fine, click next which i think should take me to my name and login etc and the colours go crazy and the screen locks up.

i tried a couple of times with restarting X but get the same every time

---

### Post by pochu on 2007-01-18
That bug is reported at Launchpad, but you can go there and confirm it!

---

### Post by ahaslam on 2007-01-18
> **petay said:**
> i have had the same problem installing

The difference is that your system isn't completely frozen, it still responds to keystrokes.
I wonder if it's the same problem, just a different result because of different hardware :-k 

The bug that relates towards your symptoms is here: [https://bugs.launchpad.net/ubuntu/+bug/78810](https://bugs.launchpad.net/ubuntu/+bug/78810)

Tony.

---

