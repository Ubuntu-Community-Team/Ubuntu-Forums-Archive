---
title: "Can a inspiron 1100 run unity-3d?"
date: 2011-12-05
forum: Desktop Environments
---

### Post by Henk506 on 2011-12-05
Is it possable to get my inspiron 1100 laptop to run unity-3d.  Personaly I think unity-2d is pretty but not very configurable.  I want something configurable.  Is it possable to get it running on this laptop.

---

### Post by wildmanne39 on 2011-12-05
Hi, please run this command in the terminal and post the results here.
```
/usr/lib/nux/unity_support_test -p
```
Thank you

---

### Post by Henk506 on 2011-12-05
/connor@OmegaThief:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.11

Not software rendered:    no
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
connor@OmegaThief:~$ 
well it is clear to me that as of right now it can not
What can i do to fix it?

---

### Post by wildmanne39 on 2011-12-05
Hi, I am not sure how old is this machine? please post the results of:
```
sudo lshw
```
Thank you

---

### Post by Henk506 on 2011-12-05
here you go

```

sudo lconnor@OmegaThief:~$ sudo lshw
[sudo] password for connor: 
omegathief                
    description: Portable Computer
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4C00-1036-8054-B2C04F473331
  *-core
       description: Motherboard
       product: 09U784
       vendor: Winbond Electronics
       physical id: 0
       serial: .2L6TG31.CN1296138U3485.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A32
          date: 10/18/2004
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.9
          slot: Microprocessor
          size: 2400MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 128KiB
             capacity: 128KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-efffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e0000000-e7ffffff memory:f6f80000-f6ffffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf40(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:11 memory:f6f7fc00-f6f7ffff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:d000(size=8192) memory:f8000000-fdffffff memory:20000000-23ffffff
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 01
                serial: 00:0d:56:35:c5:00
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:7 memory:fcffe000-fcffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:11 memory:fc000000-fc000fff ioport:d000(size=256) ioport:d400(size=256) memory:20000000-23ffffff memory:f8000000-fbffffff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
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
             product: 82801DB (ICH4) IDE Controller
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
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:24000000-240003ff
           *-cdrom
                description: DVD reader
                product: CDRW/DVD SN-324F
                vendor: SAMSUNG
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: U203
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
           *-disk
                description: ATA Disk
                product: WDC WD800BEVE-00
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 11.0
                serial: WD-WXR1AB0Y1603
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000f19a6
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 7813ed3d-ed0d-45ab-8a6f-643ebbdca648
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-11-19 17:13:26 filesystem=ext4 lastmountpoint=/ modified=2011-12-05 14:22:00 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered mounted=2011-12-05 20:10:35 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 502MiB
                   capacity: 502MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 502MiB
                      capabilities: nofs
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:7 ioport:c800(size=256) ioport:cc40(size=64) memory:f6f7f800-f6f7f9ff memory:f6f7f400-f6f7f4ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:c400(size=256) ioport:c080(size=128)
     *-network
          description: Ethernet interface
          product: DFE-690TXD CardBus PC Card
          vendor: D-Link System Inc
          physical id: 1
          bus info: pci@0000:03:00.0
          logical name: eth2
          version: 10
          serial: 00:0d:88:1b:50:19
          size: 100Mbit/s
          capacity: 100Mbit/s
          width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.23.148 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
          resources: irq:11 ioport:d000(size=256) memory:f8000000-f80001ff
  *-battery
       product: DELL 000W18
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 43000mWh
       configuration: voltage=14.8V
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: ham0
       serial: 7a:79:05:51:0a:b0
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=5.81.10.176 link=yes multicast=yes port=twisted pair speed=10Mbit/s
```

---

### Post by wildmanne39 on 2011-12-05
Hi, from what I can tell after researching it to make sure is that your video card it not supported in unity 3D it is just to old.

You can use unity 2D though.
Thank you

---

### Post by Henk506 on 2011-12-05
how about gnome 3  will it run fine plese give me something configurable that is not kde because kde is hideous in my opinion

---

### Post by wildmanne39 on 2011-12-05
Hi, I am not sure I have never used it, you can try xubuntu or lubuntu one of those should work it will help if I know what you are wanting exactly.

---

