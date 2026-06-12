---
title: "Why my System Became Slow"
date: 2012-09-21
forum: Desktop Environments
---

### Post by Mohan1289 on 2012-09-21
hey guys

I installed ubuntu through wubi

I allocated 20GB Space for the Ubuntu.

But when i started the system.

Ubuntu became very slow. If i opened application little rapidly the system is getting struck

The Configuration of the System is

250GB HDD 1GB RAM INTEL DUAL CORE PROCESSOR.

I Installed both Windows and Ubuntu in Same Drive.

What could be the problem?

:confused::confused::confused:

---

### Post by Deepak A on 2012-09-21
Did u mean ubuntu and windows on the same partition? What is its capacity?

---

### Post by Mohan1289 on 2012-09-21
The C Drive Capacity is 48.8 GB

---

### Post by Deepak A on 2012-09-21
Windows XP or 7? Have u created any swap area? there wont be much space if you are using windows 7. The capacity for windows 7 is minimum 60GB and recommended size is 120. You are running both Windows and Ubuntu in one partition. So i think there might be some problem with virtual memory paging.

---

### Post by Mohan1289 on 2012-09-21
No No i am using Windows XP not Windows 7

I don't know weather the Admin Created The SWAP AREA or not since the system belongs to the company. I hope he created it

---

### Post by Deepak A on 2012-09-21
Try running *df -h* from a terminal and verify that root having enough disk space available.

---

### Post by Mohan1289 on 2012-09-21
I Tried that it is showing it has 15 GB Free Space

---

### Post by Deepak A on 2012-09-21
You can try something like this,
1. How much memory its consuming while running? use *top* command or some gui tools.
2. Try disabling network and check the status again.
3. Read this and create a swap area of 1.5GB, if it is not created already.

[http://askubuntu.com/questions/145759/adding-swap-volume](http://askubuntu.com/questions/145759/adding-swap-volume)

4. Check if there any other machine running ubuntu 12.04 with same hardware configuration.

5. Finally if possible extend C drive capacity.

---

### Post by black veils on 2012-09-21
could be as simple as your graphics driver and unity with 1gb ram is not suitable.

if i were you, i would install another desktop environment within ubuntu. this can be done via the software center. try this one ```
xfce4
```

---

### Post by Mohan1289 on 2012-09-22
> **black veils said:**
>  try this one ```
xfce4
```



When i tried your command it's showing the following error

xfce4 command not found

---

### Post by vasa1 on 2012-09-22
> **Mohan1289 said:**
> When i tried your command it's showing the following error

xfce4 command not found
Yes, it's not a valid command, AFAIK.

BTW, why don't you dual boot instead of Wubi?

---

### Post by black veils on 2012-09-22
I said to try that desktop, not that it was the command to install it ```
sudo apt-get install xfce4
```

---

### Post by Mohan1289 on 2012-09-22
Guys i tried lshw command and Output is:

ubuntu                    
    description: Desktop Computer
    product: MS-7529 (To Be Filled By O.E.M.)
    vendor: MICRO-STAR INTERNATIONAL CO.,LTD
    version: 1.0
    serial: To Be Filled By O.E.M.
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=desktop family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=00000000-0000-0000-0000-6C626D82DA72
  *-core
       description: Motherboard
       product: G31TM-P21 (MS-7529)
       vendor: MICRO-STAR INTERNATIONAL CO.,LTD
       physical id: 0
       version: 1.0
       serial: To be filled by O.E.M.
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V4.7
          date: 07/28/2010
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) D  CPU 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) D  CPU 2.66GHz
          serial: To Be Filled By O.E.M.
          slot: CPU1
          size: 2666MHz
          capacity: 2666MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
          configuration: cores=2 enabledcores=2 threads=2
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 533 MHz (1.9 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM2
        *-bank:2
             description: DIMM [empty]
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM3
        *-bank:3
             description: DIMM [empty]
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM4
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:fea80000-feafffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fe900000-fe9fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:fea78000-fea7bfff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:1000(size=4096) memory:3f700000-3f8fffff ioport:3f900000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:feb00000-febfffff ioport:fdf00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 6c:62:6d:82:da:72
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.40.30.137 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:febe0000-febfffff
        *-usb:0
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:d880(size=32)
        *-usb:1
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d800(size=32)
        *-usb:2
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d480(size=32)
        *-usb:3
             description: USB controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d400(size=32)
        *-usb:4
             description: USB controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fea77c00-fea77fff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: N10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:d080(size=8) ioport:d000(size=4) ioport:cc00(size=8) ioport:c880(size=4) ioport:c800(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:400(size=32)
     *-scsi
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3250318AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: CC38
             serial: 5VM52JHB
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=1a7c55d9
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /host
                version: 3.1
                serial: 28d036a8-2008-e742-87cd-987b0311614f
                size: 48GiB
                capacity: 48GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2012-04-24 23:17:51 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 184GiB
                capacity: 184GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: HPFS/NTFS partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /media/mohan/D220542F20541D33
                   capacity: 184GiB
                   configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted

---

