---
title: "cdrom not seen after install"
date: 2009-03-31
forum: General Help
---

### Post by kfrancart on 2009-03-31
FIXED - Moral to the story - clean the system, especially when they are old. Remove any non-essentials (thanks kanikilu) and try again. Working currently with primary hard drive and cdrom. I'll get everything else reinstalled one step at a time. Great forum!

I'm helping a friend to move to ubuntu. After installing 8.04 lts and migrating to 8.10 the cdrom cannot be seen or even opened. 
The system is an old HP Pavilion, P3, 733MHz, 1GB mem, liteon cdrom, and DVD rom drive. All drives are seen in the bios, and I installed ubuntu using the liteon cdrom.

I've read all posts regarding cdrom to no avail. Here's what others have asked for in other posts. Hope I got it right (only been on linux for about 6 months).

Here's the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda1
UUID=6d2070c5-9f47-424e-bbf6-39703bcb3c96  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=21cd89a5-6675-46b9-9144-aa931b0eb076  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8    0  0  
/dev/sdb1                                  /media/sdb1     ntfs         defaults                    0  0  
/dev/sdb5                                  /media/sdb5     vfat         defaults                    0  0  
/dev/sda5                                  /media/sda5     swap         defaults                    0  0  

Here's the output from: sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: WDC WD400BB-75DE
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 05.0
       serial: WD-WMAD18645834
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000080
  *-disk:1
       description: ATA Disk
       product: WDC WD450AA
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 10.0
       serial: WD-WMA2E1024347
       size: 41GiB (45GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=04670466

It doesn't see the cdrom, so, any ideas?

---

### Post by kanikilu on 2009-03-31
I'm not sure, is there anything in dmesg or the other logs that might indicate a problem?

This doesn't necessarily sound like a hardware problem, but maybe try shutting down and unplugging the power from one of the drives, boot up and see if it's recognized, and then repeat with the other drive...

---

### Post by pennacook on 2009-03-31
how about just a lshw without the flags? Looks from your /etc/fstab that they are there:
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0 
```

---

### Post by kfrancart on 2009-03-31
I've disconnected the 2nd hard drive and the DVD. Now have only the primary hard drive and cdrom. Verified the cdrom opens/works prior to loading linux (the ubuntu cd works). Here's the output without the flags (wish I knew how to do the code box):

    description: Tower Computer
    product: 15133500060220
    vendor: 00101650  8760C
    version: 3
    serial: 6251HPPAV3
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=tower
  *-core
       description: Motherboard
       product: PEGASUS
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: REV 1.xx
       serial: xxxxxxxxxxx
     *-firmware
          description: BIOS
          vendor: Award Software, Inc.
          physical id: 0
          version: 1.03 (04/17/2000)
          size: 64KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi agp
     *-cpu
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.1
          slot: PGA 370
          size: 733MHz
          capacity: 800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst synchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: a
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: DIMM 2
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM DRAM Synchronous [empty]
             physical id: 2
             slot: DIMM 3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: c4
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 86c794 [Savage 3D]
                vendor: S3 Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=255 mingnt=5
        *-isa
             description: ISA bridge
             product: VT82C596 ISA [Mobile South]
             vendor: VIA Technologies, Inc.
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 4.1
             bus info: pci@0000:00:04.1
             logical name: scsi0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD400BB-75DE
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAD18645834
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00000080
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 6d2070c5-9f47-424e-bbf6-39703bcb3c96
                   size: 35GiB
                   capacity: 35GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-03-28 10:09:22 filesystem=ext3 modified=2009-03-31 12:49:01 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-31 12:46:05 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1608MiB
                   capacity: 1608MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1608MiB
                      capabilities: nofs
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 4.2
             bus info: pci@0000:00:04.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-network
             description: Ethernet interface
             product: SMC2-1211TX
             vendor: Accton Technology Corporation
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 10
             serial: 00:10:b5:57:16:66
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.11 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-multimedia
             description: Multimedia audio controller
             product: Rockwell International
             vendor: Rockwell International
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=RIPTIDE latency=32 module=snd_riptide
        *-communication UNCLAIMED
             description: Communication controller
             product: Riptide HSF 56k PCI Modem
             vendor: Rockwell International
             physical id: b.1
             bus info: pci@0000:00:0b.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=32
        *-input
             description: Input device controller
             product: Rockwell International
             vendor: Rockwell International
             physical id: b.2
             bus info: pci@0000:00:0b.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Riptide Joystick latency=0 module=snd_riptide
     *-pci:1
          description: Host bridge
          product: VT82C596 Power Management
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:04.3
          version: 30
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:12:ee:5c:f9:48
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thanks for the quick replies!

---

