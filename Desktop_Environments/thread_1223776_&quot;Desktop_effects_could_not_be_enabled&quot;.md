---
title: "&quot;Desktop effects could not be enabled&quot;"
date: 2009-07-26
forum: Desktop Environments
---

### Post by Westerberg on 2009-07-26
I would like to set up compiz desktop effects but get the above error message.
```
james@james-desktop:~/Desktop$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 
```

```
james@james-desktop:~/Desktop$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

```


```
james@james-desktop:~/Desktop$ sudo lshw
james-desktop             
    description: Desktop Computer
    product: 965P-DS3
    vendor: Gigabyte Technology Co., Ltd.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-001A4D8211B1
  *-core
       description: Motherboard
       product: 965P-DS3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F14B (07/31/2008)
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 4MiB
             capabilities: synchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM 800 MHz (1.2 ns)
             physical id: 1
             slot: A1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
        *-bank:3
             description: DIMM 800 MHz (1.2 ns)
             physical id: 3
             slot: A3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: vmx ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82P965/G965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82P965/G965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport-driver
           *-display
                description: VGA compatible controller
                product: G80 [GeForce 8800 GTS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-storage
                description: SATA controller
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: scsi0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress bus_master cap_list emulated
                configuration: driver=ahci latency=0 module=ahci
              *-disk
                   description: ATA Disk
                   product: SAMSUNG HD501LJ
                   physical id: 0.0.0
                   bus info: scsi@0:0.0.0
                   logical name: /dev/sda
                   version: CR10
                   serial: S0MUJDSP511930
                   size: 465GiB (500GB)
                   capabilities: partitioned partitioned:dos
                   configuration: ansiversion=5 signature=4caa7905
                 *-volume:0
                      description: Windows NTFS volume
                      physical id: 1
                      bus info: scsi@0:0.0.0,1
                      logical name: /dev/sda1
                      version: 3.1
                      serial: 70678ee4-aeb9-9142-9530-e9d53e5ad8f7
                      size: 48GiB
                      capacity: 48GiB
                      capabilities: primary bootable ntfs initialized
                      configuration: clustersize=4096 created=2007-08-08 00:40:11 filesystem=ntfs state=clean
                 *-volume:1
                      description: Windows NTFS volume
                      physical id: 2
                      bus info: scsi@0:0.0.0,2
                      logical name: /dev/sda2
                      version: 3.1
                      serial: 926cc47c-ca8f-df41-b9d9-975615c55235
                      size: 192GiB
                      capacity: 192GiB
                      capabilities: primary ntfs initialized
                      configuration: clustersize=4096 created=2009-06-25 15:56:29 filesystem=ntfs state=clean
                 *-volume:2
                      description: EXT3 volume
                      vendor: Linux
                      physical id: 3
                      bus info: scsi@0:0.0.0,3
                      logical name: /dev/sda3
                      version: 1.0
                      serial: c4a19364-e482-4998-b818-41f86ac6b40a
                      size: 6667MiB
                      capacity: 224GiB
                      capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files ext3 ext2 initialized
                      configuration: created=2008-11-01 15:30:50 filesystem=ext3 modified=2008-11-02 11:42:39 mounted=2008-11-02 11:08:31 state=clean
                    *-logicalvolume:0
                         description: Linux filesystem partition
                         physical id: 5
                         logical name: /dev/sda5
                         logical name: /
                         capacity: 9530MiB
                         configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
                    *-logicalvolume:1
                         description: Linux swap / Solaris partition
                         physical id: 6
                         logical name: /dev/sda6
                         capacity: 2863MiB
                         capabilities: nofs
                    *-logicalvolume:2
                         description: Linux filesystem partition
                         physical id: 7
                         logical name: /dev/sda7
                         logical name: /home
                         capacity: 212GiB
                         configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=ordered state=mounted
           *-ide
                description: IDE interface
                product: JMicron 20360/20363 AHCI Controller
                vendor: JMicron Technologies, Inc.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi6
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
              *-cdrom
                   description: DVD-RAM writer
                   product: DVDRAM GSA-H44L
                   vendor: HL-DT-ST
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: SB00
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 12
                serial: 00:1a:4d:82:11:b1
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.3 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:1e:01:67:c5:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Any help would be appreciated.

---

### Post by BillyPrefect on 2009-07-26
I just went through the same thing... uninstalled compiz manager, uninstalled the nvidia drivers and reinstalled everything.

---

### Post by ajgreeny on 2009-07-26
Certainly should be OK with that video card.  make sure you have the restricted driver enabled from **System >Administration >Hardware Drivers**, and you ought to be able to run compiz, no problem.

---

### Post by SoulTerror on 2009-07-26
I got the same error but when I first installed Ubuntu I installed the restricted video driver for my ATX card. I restarted and right after the splash screen all I had was a black screen. So reinstalled Ubuntu and didn't install the restricted driver. Is there anyway to enable this without installing the restricted drivers?

---

### Post by Westerberg on 2009-07-26
> **BillyPrefect said:**
> I just went through the same thing... uninstalled compiz manager, uninstalled the nvidia drivers and reinstalled everything.

Hmm I tried that but it didn't seem to have any effect.

```
james@james-desktop:~/Desktop$ compiz 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Here is the output of jockey.log when I try to enable Desktop effects:
> 2009-07-26 20:08:45,904 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2009-07-26 20:08:45,904 DEBUG: enables_composite(): already using nvidia driver from nondefault package
2009-07-26 20:08:45,904 DEBUG: enables_composite(): already using nvidia driver from nondefault package


---

### Post by ColonelCommandLine on 2009-07-26
Uninstall Compiz and your driver, then reinstall

---

