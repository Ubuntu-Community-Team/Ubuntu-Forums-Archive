---
title: "Dependency problems prevent configuration of linux-image-generic"
date: 2014-12-12
forum: Desktop Environments
---

### Post by mollie4168 on 2014-12-12
I'm on an old Dell Inspiron 1525 that is going to be replaced in a couple weeks, but I'd still like to make it until then.  My software updates haven't been working for the past few weeks (and I didn't try to look into it since I knew this computer was on its way out), and now it's at the point where I can't update flash or anything else.  It seems like something is configured incorrectly, but that's beyond my knowledge.  I don't understand "gzip: stdout: No space left on device." since the general memory on the computer is only 30% used.  Also, the computer keeps utterly freezing on me, and I'm not sure how much of this is all the same problem vs age.

Here's some information to get a sense of what's going on.  Thank you for any help.

$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  freeglut3 grass-doc libmotif-common libmrm4 libqgisgrass2.0.1 libtk8.5
  libuil4 libxm4 linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
  python-opengl qgis-plugin-grass-common tk8.5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-3.13.0-40-generic (3.13.0-40.69) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-40-generic /boot/vmlinuz-3.13.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-40-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-40-generic; however:
  Package linux-image-extra-3.13.0-40-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.40.47); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-40-generic
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-40-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schragge on 2014-12-12
Most probably, you have a separate /boot partition, and it is full with old kernel images. See [thread=2256452]this thread[/thread]. Look at the output of
```
df -h
```

You can make some space with
```
sudo apt-get autoremove
```

---

### Post by mollie4168 on 2014-12-12
Thank you for the other thread.  I'll take a look at it and try the suggestions.

```
$ df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/xubuntu--vg-root  109G   29G   75G  28% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          483M  4.0K  483M   1% /dev
tmpfs                         100M  1.2M   99M   2% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          497M  572K  496M   1% /run/shm
none                          100M   28K  100M   1% /run/user
/dev/sdb1                     236M  228M     0 100% /boot
/home//.Private               109G   29G   75G  28% /home/
```

---

### Post by schragge on 2014-12-12
Yep. This line:
```
/dev/sdb1 236M 228M 0 [color=red]100%[/color] /boot
```

---

### Post by mörgæs on 2014-12-13
> **mollie4168 said:**
> ... Dell Inspiron 1525 that is going to be replaced in a couple weeks

Why? If you feed it X/Lubuntu it will be an excellent computer.

---

### Post by mollie4168 on 2014-12-13
The problems have improved, so thank you for pointing me in the right direction, schragge.

Moraeges, I installed Xubuntu a few months ago, cleaned everything out and it's still really slow.  I'm assuming the hardware has run its course, but what are your thoughts?  The decision to get a new computer was made by someone else, and it's already done, but please share your knowledge so I can keep the next one going as long as possible.  This Dell is 6.5 years old.

---

### Post by mörgæs on 2014-12-13
In my world 6,5 years means new. 

Let's see the specifications. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by mollie4168 on 2014-12-14
```
computer
    description: Portable Computer
    product: Inspiron 1525 ()
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 0U990C
       vendor: Dell Inc.
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A11
          date: 03/10/2008
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.15.13
          serial: [REMOVED]
          slot: Microprocessor
          size: 800MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: cores=2 enabledcores=2 id=1 threads=2
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
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
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: HYMP564S64CP6-Y5
             vendor: Hynix Semiconductor (Hyundai Electronics)
             physical id: 0
             serial: [REMOVED]
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous
             vendor: FFFFFFFFFFFFFFFF
             physical id: 1
             serial: [REMOVED]
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
     *-generic UNCLAIMED
          physical id: 1
          bus info: parisc@0
        *-generic:0 UNCLAIMED
             physical id: 1
             bus info: parisc@1
        *-generic:1 UNCLAIMED
             physical id: 10
             bus info: parisc@10
        *-generic:2 UNCLAIMED
             physical id: 11
             bus info: parisc@11
        *-generic:3 UNCLAIMED
             physical id: 2
             bus info: parisc@2
        *-generic:4 UNCLAIMED
             physical id: 3
             bus info: parisc@3
        *-generic:5 UNCLAIMED
             physical id: 4
             bus info: parisc@4
        *-generic:6 UNCLAIMED
             physical id: 5
             bus info: parisc@5
        *-generic:7 UNCLAIMED
             physical id: 6
             bus info: parisc@6
        *-generic:8 UNCLAIMED
             physical id: 7
             bus info: parisc@7
        *-generic:9 UNCLAIMED
             physical id: 8
             bus info: parisc@8
        *-generic:10 UNCLAIMED
             physical id: 9
             bus info: parisc@9
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
             resources: irq:44 memory:fea00000-feafffff memory:e0000000-efffffff ioport:eff8(size=8)
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
             resources: memory:feb00000-febfffff
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f20(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f00(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:fed1c400-fed1c7ff
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
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:fe9fc000-fe9fffff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fe800000-fe8fffff ioport:40000000(size=2097152)
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 12
                serial: [REMOVED]
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=4096) memory:fe700000-fe7fffff ioport:40200000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: wlan0
                version: 02
                serial: [REMOVED]
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.13.0-43-generic firmware=15.32.2.9 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:47 memory:fe7ff000-fe7fffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:fe400000-fe6fffff ioport:f0000000(size=2097152)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:6f80(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:6f60(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:6f40(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:fed1c000-fed1c3ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:fe300000-fe3fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:16 memory:fe3ff800-fe3fffff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:02:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:fe3ff400-fe3ff4ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:02:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:18 memory:fe3ff600-fe3ff6ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:02:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:18 memory:fe3ff700-fe3ff7ff
        *-isa
             description: ISA bridge
             product: 82801HM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:6fa0(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:6eb0(size=8) ioport:6eb8(size=4) ioport:6ec0(size=8) ioport:6ec8(size=4) ioport:6ee0(size=32) memory:fe9fb800-fe9fbfff
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
             resources: memory:fe9fb700-fe9fb7ff ioport:10c0(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW AD-5560A
             vendor: Optiarc
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: DD11
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom
     *-scsi:1
          physical id: 3
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1200BEVS-7
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000e509b
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: [REMOVED]
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable extended_attributes ext2 initialized
                configuration: filesystem=ext2 lastmountpoint=/boot modified=2014-12-14 09:10:36 mount.fstype=ext2 mount.options=rw,relatime mounted=2014-12-14 09:10:36 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 111GiB
                capacity: 111GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 111GiB
  *-battery
       product: DELL 00
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 66000mWh
       configuration: voltage=10.8V
```

---

### Post by mörgæs on 2014-12-14
Looks good. I suggest a fresh install of a 32 bit Lubuntu 14.04.1 or 14.10. 

If you happen to find some more RAM modules it's an easy way of speeding up the system. See also this:
[http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289](http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289)

---

### Post by Yellow Pasque on 2014-12-15
That system shouldn't be slow running Xubuntu or Lubuntu. You only have 1GB of RAM, so that can be a bit limiting, even with X/Lubuntu. Did you also set up a swap partition when you installed?

The system came with 2*512MB DDR2-667 (aka PC2-5300) modules. If you don't mind spending a bit of money, you could swap them out for 2*1GB or 2*2GB sticks. I didn't save the link, but I saw a claim that this system can also use DDR2-800 (PC2-6400) if the BIOS is up to date. Given that Dell lists DDR2-800 modules as replacement parts for this model on its support site, I would believe that.

It looks like you can get 2*2GB for about $40. I didn't really see great deals on 2*1GB ($25-30), but I only looked at amazon and newegg.
[http://www.amazon.com/Dell-200-pin-PC2-6400-unbuffered-non-ECC/dp/B001R84DIY/](http://www.amazon.com/Dell-200-pin-PC2-6400-unbuffered-non-ECC/dp/B001R84DIY/)

Oh, and I think it would be worth it to look at the SMART info for the disk and make sure it's not dying. Assuming your disk is /dev/sda
```
sudo smartctl -a /dev/sda -q noserial
```

---

### Post by mollie4168 on 2014-12-21
> **mörgæs said:**
> Looks good. I suggest a fresh install of a 32 bit Lubuntu 14.04.1 or 14.10. 

If you happen to find some more RAM modules it's an easy way of speeding up the system. See also this:
[http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289](http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289)

Mörgæs, thank you very much for this information.  I will keep it in mind for the future.  I wish I had known a few months ago that there were options, like getting more RAM.  


                  [INDENT]                                                        >  That system shouldn't be slow running Xubuntu or Lubuntu. You only  have 1GB of RAM, so that can be a bit limiting, even with X/Lubuntu. Did  you also set up a swap partition when you installed?

The system came with 2*512MB DDR2-667 (aka PC2-5300) modules. If you  don't mind spending a bit of money, you could swap them out for 2*1GB or  2*2GB sticks. I didn't save the link, but I saw a claim that this  system can also use DDR2-800 (PC2-6400) if the BIOS is up to date. Given  that Dell lists DDR2-800 modules as replacement parts for this model on  its support site, I would believe that.

It looks like you can get 2*2GB for about $40. I didn't really see great  deals on 2*1GB ($25-30), but I only looked at amazon and newegg.
[http://www.amazon.com/Dell-200-pin-P...dp/B001R84DIY/]("http://www.amazon.com/Dell-200-pin-PC2-6400-unbuffered-non-ECC/dp/B001R84DIY/")

Oh, and I think it would be worth it to look at the SMART info for the  disk and make sure it's not dying. Assuming your disk is /dev/sda
     Code:
     sudo smartctl -a /dev/sda -q noserial



Temüjin, I tried your command, and it could not find the smartctl command. 
         [/INDENT]

---

### Post by Yellow Pasque on 2014-12-21
> **mollie4168 said:**
> Temüjin, I tried your command, and it could not find the smartctl command.
You reminded me that I forgot:
```
sudo apt-get install smartmontools
```

---

