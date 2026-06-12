---
title: "Dell vostro 1310 won't hibernate"
date: 2011-07-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wh1zz0 on 2011-07-30
Hello guys,

Ever since I installed Ubuntu my machine has refused to hibernate. When I noticed this I thought it was a simple issue I had to simply set in my "Power Management" but this was not the case as everything there is properly set not to go into suspension at all. In fact I set it to hibernate when the battery is low or almost empty but it doesn't do what I ask it to do. Instead it suspends! :( I need help because this is really frustrating for me as anytime my battery gets low it just either enters suspend mode (with two led lights flashing continuously with no way to resume) or it just goes off entirely. In both cases I end up losing ALL my data and this is killing me. If this goes on like this my hard disk may become damaged after sometime. Please I need your help. 

I found various tutorials but not all seem to work. The closest tutorial I found relating to my problem is this: [http://ubuntuforums.org/showthread.php?t=850755](http://ubuntuforums.org/showthread.php?t=850755) .. In this tutorial the guy (empty _tank) says we should edit the file named menu.lst right in /boot/grub/ but I checked and there is no file like that in my grub folder. And when I try ```
gksu gedit /boot/grub/menu.lst
``` I get the following error ```
@linux-box:~# gksu gedit /boot/grub/menu.lst

(gedit:3379): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.X04TZV': No such file or directory

(gedit:3379): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3379): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.H2ZTZV': No such file or directory

(gedit:3379): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
``` and an empty file opens up named menu.lst (so you see it's creating it for the first time so I just close it back).

I went into the #ubuntu IRC to ask for help but to no avail. Someone in there (nit-wit) asked me to check if I have enough swap. So I installed gparted and here is the screenshot which says that I do have sufficient: [http://imagebin.org/165641](http://imagebin.org/165641)

In the tutorial the guy says we should edit the menu.lst file in /boot/grub but there's no such file in natty

This is really killing me, I have been battling with this for over 1 week now but still haven't got any solution. Please I want my machine to be able to hibernate or even sleep so that It can resume properly without losing all my data and weakening my hard disk by sudden power offs. Please help....

========
PC OS: Ubuntu 11.4
LAPTOP: Dell Vostro 1310
RAM: 2Gig

FULL:: 

```
    description: Portable Computer
    version: Null
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=oem-specific chassis=portable cpus=2 family=Vostro sku=Null
  *-core
       description: Motherboard
       product: 0H528C
       vendor: Winbond Electronics
       physical id: 0
       serial: .4WXCVF1.CN1296188U0060.
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 1
          version: A10
          date: 07/10/2008
          size: 107KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: U2E1
          size: 1801MHz
          capacity: 1801MHz
          width: 64 bits
          clock: 800MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 6
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 7
             size: 2MiB
             capacity: 4MiB
             capabilities: burst internal write-back
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
          physical id: 11
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: V916765G24QCFW-F5
             vendor: ProMOS/Mosel Vitelic
             physical id: 0
             serial: 7E8206D9
             slot: JDIM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: V916765G24QCFW-F5
             vendor: ProMOS/Mosel Vitelic
             physical id: 1
             serial: CC8206DA
             slot: JDIM2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-cpu:1
          physical id: 0
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1800MHz
          capacity: 1800MHz
          capabilities: ht cpufreq
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
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:46 memory:f8000000-f80fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f8100000-f81fffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:f8504800-f8504bff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:f8500000-f8503fff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:c4000000-c7ffffff ioport:cc000000(size=33554432)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:f0000000-f3ffffff ioport:fa000000(size=33554432)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:f4000000-f7ffffff ioport:fc000000(size=33554432)
           *-network DISABLED
                description: Wireless interface
                product: BCM4312 802.11b/g LP-PHY
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:06:00.0
                logical name: eth1
                version: 01
                serial: 00:22:69:3f:0c:18
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:19 memory:f4000000-f4003fff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:80000000-803fffff ioport:f8600000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 02
                serial: 00:21:70:ac:16:40
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:45 ioport:5000(size=256) memory:f8610000-f8610fff memory:f8600000-f860ffff memory:f8620000-f862ffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f8504c00-f8504fff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:f8200000-f82fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 5
                bus info: pci@0000:08:05.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64
                resources: irq:22 memory:f8200000-f8200fff memory:f8202000-f82027ff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 5.2
                bus info: pci@0000:08:05.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=32
                resources: irq:22 memory:f8202800-f82028ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 5.3
                bus info: pci@0000:08:05.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm cap_list
                configuration: latency=32
                resources: memory:f8201000-f8201fff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: DVD+-RW UJ-875S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: D200
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:1c00(size=8) ioport:18d4(size=4) ioport:18d8(size=8) ioport:18d0(size=4) ioport:18e0(size=32) memory:f8504000-f85047ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-7
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXE608FM7144
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004453c
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9470f64a-2a1c-4af3-b53e-a02db850d15f
                   size: 230GiB
                   capacity: 230GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-07-12 10:18:13 filesystem=ext4 lastmountpoint=/ modified=2011-07-23 12:41:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered mounted=2011-07-30 08:51:58 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2037MiB
                   capacity: 2037MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2037MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:80400000-804000ff ioport:1c20(size=32)
  *-battery
       description: Lithium Ion Battery
       product: SANYO     06/01/01
       vendor: SANYO     06/01/01
       physical id: 1
       slot: Rear
       capacity: 57720mWh
       configuration: voltage=11.1V
```

=====

Thanks in anticipation of any swift response...

Kind regards,
Wh1zz0

---

### Post by mikewhatever on 2011-07-30
The tutorial is a bit old, Ubuntu doesn't have the menu.lst file since 9.10. That said, you can still add the suggested boot option - resume=/dev/sda5 - by by editing your /etc/default/grub file instead. Your line to add your boot options should look like your this:
```
GRUB_CMDLINE_LINUX=""

```

...add your boot options in between your quotes.:P
Update your grub when done with **sudo update-grub**

If your swap partition is not your problem, check out your pm-suspend.log in your /var/log.

---

### Post by wh1zz0 on 2012-01-19
> **mikewhatever said:**
> The tutorial is a bit old, Ubuntu doesn't have the menu.lst file since 9.10. That said, you can still add the suggested boot option - resume=/dev/sda5 - by by editing your /etc/default/grub file instead. Your line to add your boot options should look like your this:
```
GRUB_CMDLINE_LINUX=""

```

...add your boot options in between your quotes.:P
Update your grub when done with **sudo update-grub**

If your swap partition is not your problem, check out your pm-suspend.log in your /var/log.

Thanks for your response, though I noticed it quite late. I upgraded to oneiric and still experiencing the same problem. Instead of hibernating, my machine goes into suspension and there's no way to resume previous session unless I hold down the power button to shutdown.. And sadly, I end up losing all unsaved data/work. 

As per your response, what boot option am I supposed to add? Am I supposed to modify my /etc/default/grub file, appending this?? ```
GRUB_CMDLINE_LINUX="resume=/dev/sda5"
```If otherwise, please clarify specifically.

Thanks in anticipation of your swift response.

Kind regards..

---

### Post by wh1zz0 on 2012-01-19
P.S.... Below is the output of ```
cat /var/log/pm-suspend.log
``` and ```
cat /var/log/pm-suspend.log.1
``` respectively:

[http://paste.ubuntu.com/809825/](http://paste.ubuntu.com/809825/)

[http://paste.ubuntu.com/809828/](http://paste.ubuntu.com/809828/)

Thanks again...

---

