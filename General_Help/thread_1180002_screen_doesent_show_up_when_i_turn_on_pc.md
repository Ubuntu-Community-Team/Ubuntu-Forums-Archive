---
title: "screen doesent show up when i turn on pc"
date: 2009-06-06
forum: General Help
---

### Post by demon_hunter on 2009-06-06
when i turn on my pc the screen wont show up it just says "no signal" 

any help

---

### Post by Legace on 2009-06-06
> **demon_hunter said:**
> when i turn on my pc the screen wont show up it just says "no signal" 

any help

Don't you see **any**thing?

Make sure the wire that connects your PC and your monitor is connected properly.

---

### Post by dharvell on 2009-06-06
> **demon_hunter said:**
> when i turn on my pc the screen wont show up it just says "no signal" 

any help
"No Signal" is usually your monitor's way of telling you that it IS not or CAN not receive a signal from your computer with the current configuration.  This said, you probably have a problem within your configuration of X-server.

If you can boot your computer into recovery mode, check your X configuration compared to your monitors capability (usually printed on back of monitor... if not, read the manual that came with your monitor).

Your X configuration is usually at:
/etc/X11/xorg.conf

---

### Post by Legace on 2009-06-06
Do you see a POST message?
Something like this: [http://www.fitzenreiter.de/ata/asus-a7n8x-deluxe-bios-post.gif](http://www.fitzenreiter.de/ata/asus-a7n8x-deluxe-bios-post.gif)

---

### Post by demon_hunter on 2009-06-06
the only thing i see is hte words "no signal" and then it go's blank and wont do anything

---

### Post by dharvell on 2009-06-06
> **demon_hunter said:**
> the only thing i see is hte words "no signal" and then it go's blank and wont do anything

And everything is plugged in, correctly?

If you are plugged in correctly, can you give us an idea of your computer's specs?

---

### Post by demon_hunter on 2009-06-06
here is the specs 

```

description: Desktop Computer
product: Advent Series
vendor: TriGem Computer NETHERLANDS
width: 32 bits
capabilities: smbios-2.2 dmi-2.2 smp
configuration: boot=normal chassis=desktop
*-core
description: Motherboard
product: SiS-645
physical id: 0
*-firmware
description: BIOS
vendor: Award Software International, Inc.
physical id: 0
version: 6.00 PG (03/26/2002)
size: 128KiB
capacity: 192KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
*-cpu
description: CPU
product: Intel(R) Pentium(R) 4 CPU 2.00GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 15.1.2
slot: Socket 478
size: 2GHz
capacity: 2200MHz
width: 32 bits
clock: 100MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
configuration: id=0
*-cache:0
description: L1 cache
physical id: a
slot: Internal Cache
size: 8KiB
capacity: 20KiB
capabilities: synchronous internal write-back
*-cache:1 DISABLED
description: L2 cache
physical id: b
slot: External Cache
size: 256KiB
capacity: 256KiB
capabilities: synchronous external write-back
*-memory
description: System Memory
physical id: 1b
slot: System board or motherboard
size: 512MiB
capacity: 1GiB
*-bank:0
description: DIMM
physical id: 0
slot: A0
size: 256MiB
*-bank:1
description: DIMM
physical id: 1
slot: A1
size: 256MiB
*-bank:2
description: DIMM [empty]
physical id: 2
slot: A2
*-bank:3
description: DIMM [empty]
physical id: 3
slot: A3
*-pci
description: Host bridge
product: SiS645 Host & Memory & AGP Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 100
bus info: pci@0000:00:00.0
version: 01
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-sis latency=32 module=sis_agp
*-pci
description: PCI bridge
product: Virtual PCI-to-PCI bridge (AGP)
vendor: Silicon Integrated Systems [SiS]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master
*-display
description: VGA compatible controller
product: NV17 [GeForce4 MX 420]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
*-isa
description: ISA bridge
product: SiS961 [MuTIOL Media IO]
vendor: Silicon Integrated Systems [SiS]
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: isa bus_master
configuration: latency=0
*-serial
description: SMBus
product: SiS961/2 SMBus Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.1
bus info: pci@0000:00:02.1
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
*-usb:0
description: USB Controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.2
bus info: pci@0000:00:02.2
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
*-usb:1
description: USB Controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.3
bus info: pci@0000:00:02.3
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
*-ide
description: IDE interface
product: 5513 [IDE]
vendor: Silicon Integrated Systems [SiS]
physical id: 2.5
bus info: pci@0000:00:02.5
logical name: scsi0
logical name: scsi1
version: d0
width: 32 bits
clock: 33MHz
capabilities: ide bus_master emulated
configuration: driver=pata_sis latency=128 module=pata_sis
*-disk
description: ATA Disk
product: SAMSUNG SV4002H
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: QP20
serial: 0358J1FT392289
size: 37GiB (40GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=ad7dad7d
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
logical name: /dev/.static/dev
version: 1.0
serial: 189c5c8c-616e-48fc-8c49-78208c1f8577
size: 35GiB
capacity: 35GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration: created=2008-07-19 21:38:00 filesystem=ext3 modified=2008-08-10 12:19:48 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-10 12:19:48 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
size: 1466MiB
capacity: 1466MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 1466MiB
capabilities: nofs
*-cdrom:0
description: DVD reader
product: DVD-ROM SD-616T
vendor: SAMSUNG
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: F300
capabilities: removable audio dvd
configuration: ansiversion=5 status=open
*-cdrom:1
description: CD-R/CD-RW writer
product: CD-RW GCE-8320B
vendor: HL-DT-ST
physical id: 0.1.0
bus info: scsi@1:0.1.0
logical name: /dev/cdrom1
logical name: /dev/scd1
logical name: /dev/sr1
version: 1.02
capabilities: removable audio cd-r cd-rw
configuration: ansiversion=5 status=open
*-multimedia
description: Multimedia audio controller
product: AC'97 Sound Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.7
bus info: pci@0000:00:02.7
version: a0
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
*-communication UNCLAIMED
description: Communication controller
product: HSF 56k HSFi Modem
vendor: Conexant
physical id: a
bus info: pci@0000:00:0a.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=32
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: d
bus info: pci@0000:00:0d.0
logical name: eth0
version: 10
serial: 00:07:95:e8:09:08
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.68 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by overdrank on 2009-06-06
Ok when did this issue start, after some updates?
What version of Ubuntu are your using, Jaunty 9.04?
Are you able to see the grub loading screen?
I see your system has two graphics cards  NV17 [GeForce4 MX 420]
and SIS integrated. Is the cable connect to the correct output?

---

### Post by dharvell on 2009-06-06
You have been asked twice if you had made sure that your monitor was plugged in correctly.  You've answered every question except that one. :)

Looks like you're using an nVidia video card.  IF you have everything plugged in, correctly and you see everything that you would expect to see while your computer is booting, you may not have the correct video driver installed.  This could cause all sorts of unusual havoc.

> **demon_hunter said:**
> here is the specs 

```

description: Desktop Computer
product: Advent Series
vendor: TriGem Computer NETHERLANDS
width: 32 bits
capabilities: smbios-2.2 dmi-2.2 smp
configuration: boot=normal chassis=desktop
*-core
description: Motherboard
product: SiS-645
physical id: 0
*-firmware
description: BIOS
vendor: Award Software International, Inc.
physical id: 0
version: 6.00 PG (03/26/2002)
size: 128KiB
capacity: 192KiB
capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
*-cpu
description: CPU
product: Intel(R) Pentium(R) 4 CPU 2.00GHz
vendor: Intel Corp.
physical id: 4
bus info: cpu@0
version: 15.1.2
slot: Socket 478
size: 2GHz
capacity: 2200MHz
width: 32 bits
clock: 100MHz
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
configuration: id=0
*-cache:0
description: L1 cache
physical id: a
slot: Internal Cache
size: 8KiB
capacity: 20KiB
capabilities: synchronous internal write-back
*-cache:1 DISABLED
description: L2 cache
physical id: b
slot: External Cache
size: 256KiB
capacity: 256KiB
capabilities: synchronous external write-back
*-memory
description: System Memory
physical id: 1b
slot: System board or motherboard
size: 512MiB
capacity: 1GiB
*-bank:0
description: DIMM
physical id: 0
slot: A0
size: 256MiB
*-bank:1
description: DIMM
physical id: 1
slot: A1
size: 256MiB
*-bank:2
description: DIMM [empty]
physical id: 2
slot: A2
*-bank:3
description: DIMM [empty]
physical id: 3
slot: A3
*-pci
description: Host bridge
product: SiS645 Host & Memory & AGP Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 100
bus info: pci@0000:00:00.0
version: 01
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-sis latency=32 module=sis_agp
*-pci
description: PCI bridge
product: Virtual PCI-to-PCI bridge (AGP)
vendor: Silicon Integrated Systems [SiS]
physical id: 1
bus info: pci@0000:00:01.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pci normal_decode bus_master
*-display
description: VGA compatible controller
product: NV17 [GeForce4 MX 420]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: a3
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
*-isa
description: ISA bridge
product: SiS961 [MuTIOL Media IO]
vendor: Silicon Integrated Systems [SiS]
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: isa bus_master
configuration: latency=0
*-serial
description: SMBus
product: SiS961/2 SMBus Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.1
bus info: pci@0000:00:02.1
version: 00
width: 32 bits
clock: 33MHz
configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
*-usb:0
description: USB Controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.2
bus info: pci@0000:00:02.2
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
*-usb:1
description: USB Controller
product: USB 1.1 Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.3
bus info: pci@0000:00:02.3
version: 07
width: 32 bits
clock: 33MHz
capabilities: ohci bus_master
configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
*-ide
description: IDE interface
product: 5513 [IDE]
vendor: Silicon Integrated Systems [SiS]
physical id: 2.5
bus info: pci@0000:00:02.5
logical name: scsi0
logical name: scsi1
version: d0
width: 32 bits
clock: 33MHz
capabilities: ide bus_master emulated
configuration: driver=pata_sis latency=128 module=pata_sis
*-disk
description: ATA Disk
product: SAMSUNG SV4002H
physical id: 0
bus info: scsi@0:0.0.0
logical name: /dev/sda
version: QP20
serial: 0358J1FT392289
size: 37GiB (40GB)
capabilities: partitioned partitioned:dos
configuration: ansiversion=5 signature=ad7dad7d
*-volume:0
description: EXT3 volume
vendor: Linux
physical id: 1
bus info: scsi@0:0.0.0,1
logical name: /dev/sda1
logical name: /
logical name: /dev/.static/dev
version: 1.0
serial: 189c5c8c-616e-48fc-8c49-78208c1f8577
size: 35GiB
capacity: 35GiB
capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration: created=2008-07-19 21:38:00 filesystem=ext3 modified=2008-08-10 12:19:48 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-08-10 12:19:48 state=mounted
*-volume:1
description: Extended partition
physical id: 2
bus info: scsi@0:0.0.0,2
logical name: /dev/sda2
size: 1466MiB
capacity: 1466MiB
capabilities: primary extended partitioned partitioned:extended
*-logicalvolume
description: Linux swap / Solaris partition
physical id: 5
logical name: /dev/sda5
capacity: 1466MiB
capabilities: nofs
*-cdrom:0
description: DVD reader
product: DVD-ROM SD-616T
vendor: SAMSUNG
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: F300
capabilities: removable audio dvd
configuration: ansiversion=5 status=open
*-cdrom:1
description: CD-R/CD-RW writer
product: CD-RW GCE-8320B
vendor: HL-DT-ST
physical id: 0.1.0
bus info: scsi@1:0.1.0
logical name: /dev/cdrom1
logical name: /dev/scd1
logical name: /dev/sr1
version: 1.02
capabilities: removable audio cd-r cd-rw
configuration: ansiversion=5 status=open
*-multimedia
description: Multimedia audio controller
product: AC'97 Sound Controller
vendor: Silicon Integrated Systems [SiS]
physical id: 2.7
bus info: pci@0000:00:02.7
version: a0
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
*-communication UNCLAIMED
description: Communication controller
product: HSF 56k HSFi Modem
vendor: Conexant
physical id: a
bus info: pci@0000:00:0a.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=32
*-network
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: d
bus info: pci@0000:00:0d.0
logical name: eth0
version: 10
serial: 00:07:95:e8:09:08
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.68 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by Harpie Queen on 2009-06-06
Check if there is any dust in the ports. What I learnt from Gameboy colour =P. If there is blow in them. Then try again, being careful to put the cable in properly. If that does not work, try using your monitor with another computer, or your computer with another monitor, to identify where the problem lies. Then talk to someone who knows more than me.

---

