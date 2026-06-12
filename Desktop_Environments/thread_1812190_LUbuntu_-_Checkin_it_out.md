---
title: "LUbuntu - Checkin it out"
date: 2011-07-25
forum: Desktop Environments
---

### Post by phosphide on 2011-07-25
I started using lubuntu and I gotta tell ya, this is running smoking hot on my system. Though, I was curious, what are the limits of this thing? Do any of yall use it?

Noticing that Libreoffice isn't initially installed. Can it run that ok?

Just looking for some opinions. Really liking it so far.

---

### Post by trollolo on 2011-07-25
as far as i know, it's just ubuntu with a different DE/WM

what's so amazing about it OP?

---

### Post by ve4cib on 2011-07-25
Lubuntu is designed to be a lighter-weight remix for hardware that simply can't handle Unity/Gnome, KDE, or even XFCE.  It uses lighter alternatives for some applications when possible (I believe it uses Gnumeric as its default spreadsheet program as an example), and uses LXDE instead of Gnome or KDE as its default WM.

However, underneath the hood it's still Ubuntu.  It uses the same repos, and has access to the same packages.  If you have enough RAM and CPU to run LibreOffice (which is likely) then yes, it will run those applications just fine.  It will likely pull in a lot of dependencies, increasing the disk space used by the system.

I haven't personally used Lubuntu much.  I was on the mailing list back when it was first proposed, but got fed up with it when flame wars erupted over the very concept of including Qt so that they could use VLC as the default media player instead of Totem/Gnome-Mplayer/etc...  Ideologies often get in the way of adpoting a good idea.

Anyway, from what little I've done with it, it seems like a pretty decent remix.  I've been debating using again when 11.10 or 12.04 is released.

---

### Post by phosphide on 2011-07-26
I can't believe how fast it is running. Granted I haven't done anything major yet, but for just off a usb stick I'm pretty satisfied. Installing flash was a quick command and now I'm just playing around.

Here are my specs:

 ```
ubuntu                    
    description: Notebook
    version: F.0B
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=RM297UT#ABA uuid=19076695-4B15-E011-0394-6D9910046129
  *-core
       description: Motherboard
       product: 30C5
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 71.36
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: 68MVD Ver. F.0B
          date: 12/07/2007
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.11
          serial: 0000-06FB-0000-0000-0000-0000
          slot: U10
          size: 2201MHz
          capacity: 2201MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm ida tpr_shadow vnmi flexpriority cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal L2 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: burst external write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-667E1
             vendor: Micron Technology
             physical id: 0
             serial: EA01EF6D
             slot: DIMM #1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: DIMM #2
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=4096) memory:e5000000-e7ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G84M [Quadro FX 570M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:16 memory:e5000000-e5ffffff memory:d0000000-dfffffff memory:e6000000-e7ffffff ioport:4000(size=128)
        *-communication:0 UNCLAIMED
             description: Communication controller
             product: Mobile PM965/GM965 MEI Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:e8000000-e800000f
        *-ide:0
             description: IDE interface
             product: Mobile PM965/GM965 PT IDER Controller
             vendor: Intel Corporation
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list
             configuration: driver=ata_generic latency=0
             resources: irq:18 ioport:5000(size=8) ioport:5008(size=4) ioport:5010(size=8) ioport:5018(size=4) ioport:5020(size=16)
        *-communication:1
             description: Serial controller
             product: Mobile PM965/GM965 KT Controller
             vendor: Intel Corporation
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 0c
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:17 ioport:5030(size=8) memory:e8001000-e8001fff
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:1a:4b:7c:0a:98
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:44 memory:e8020000-e803ffff memory:e8040000-e8040fff ioport:5040(size=32)
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
             resources: irq:16 ioport:5060(size=32)
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
             resources: irq:17 ioport:5080(size=32)
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
             resources: irq:18 memory:e8041000-e80413ff
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
             resources: irq:47 memory:e8044000-e8047fff
        *-pci:1
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
             resources: irq:41
        *-pci:2
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
             resources: irq:42 ioport:6000(size=4096) memory:e4000000-e40fffff ioport:88000000(size=2097152)
           *-network
                description: Wireless interface
                product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wlan0
                version: 61
                serial: 00:1d:e0:a4:c3:e3
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 ip=192.168.1.71 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:46 memory:e4000000-e4001fff
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
             resources: irq:43 ioport:2000(size=8192) memory:e0000000-e3ffffff ioport:88200000(size=2097152)
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
             resources: irq:20 ioport:50a0(size=32)
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
             resources: irq:22 ioport:50c0(size=32)
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
             resources: irq:18 ioport:50e0(size=32)
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
             resources: irq:20 memory:e8048000-e80483ff
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
             resources: ioport:7000(size=4096) memory:e4100000-e43fffff ioport:80000000(size=134217728)
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:02:06.0
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00303020-b0030301f irq:16 memory:e4100000-e4100fff ioport:7000(size=256) ioport:7400(size=256) memory:80000000-83ffffff memory:8c000000-8fffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:02:06.1
                version: b9
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: iomemory:b00704020-b0070401f irq:17 memory:e4101000-e4101fff ioport:7800(size=256) ioport:7c00(size=256) memory:84000000-87ffffff memory:90000000-93ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:02:06.2
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:18 memory:e4102000-e41027ff
           *-generic
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:02:06.3
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:19 memory:e4103000-e41030ff
        *-isa
             description: ISA bridge
             product: 82801HBM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:1
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
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:5100(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: BD-MLT UJ-210S
                vendor: MATSHITA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/THE_DARK_NIGHT
                version: 1.24
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/THE_DARK_NIGHT
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=999,gid=999,umask=77,dmode=500,iocharset=utf8 state=mounted
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi5
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:13f0(size=8) ioport:15f4(size=4) ioport:1370(size=8) ioport:1574(size=4) ioport:5140(size=32) memory:e8049000-e80497ff
           *-disk
                description: ATA Disk
                product: FUJITSU MHW2120B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@5:0.0.0
                logical name: /dev/sda
                version: 891B
                serial: K30XT8125UEY
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=95aa95aa
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: 7ef52e46-5202-4a92-9d1a-6e8be12da637
                   size: 107GiB
                   capacity: 107GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2011-02-17 21:17:00 filesystem=ext3 modified=2011-07-15 03:04:48 mounted=2011-07-26 02:07:58 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: /dev/sda2
                   size: 4690MiB
                   capacity: 4690MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 4690MiB
                      capabilities: nofs
     *-scsi
          physical id: 1
          bus info: usb@2:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 3823MiB (4008MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=000a110d
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /cdrom
                version: FAT32
                serial: f0c2-87ed
                size: 3821MiB
                capacity: 3821MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
  *-battery
       description: Lithium Ion Battery
       product: HP
       vendor: Hewlett-Packard
       physical id: 1
       version: 11/25/2010
       serial: 00877
       slot: Primary
       capacity: 52000mWh
       configuration: voltage=14.8V

```

To be honest, I don't need a huge demand from my linux machines. Especially with the cloud options available now, I have been waiting for something kinda like the Chromium OS concept. This appears to be my answer. Easily able to get into my windows skydrive just incase I need to make win docs, google docs worked, and I'm about to see how well the Ubuntu one syncs.

---

### Post by BrokenKingpin on 2011-07-27
I have tried Lubuntu on my netbook and I really liked it. It was really fast, and had no real issues with it. The main reason I didn't stick with it is because there is currently no official 64-bit version.

I still find Xubuntu to be a more complete package, and offers more configuration utilities. It is not as fast as Lubuntu (but still quite fast), but it feels like a more complete package.

---

### Post by MG&amp;TL on 2011-07-27
It is insanely fast when compared to ubuntu, or even xubuntu. I have absolutely no idea why though. It looks awful, and customization is limited, but it is very usable, and is the fastest 'usable' OS I have installed.

---

### Post by drawkcab on 2011-07-27
2 random observations:

1.  As Xubuntu bloats up, Lubuntu is filling in as needed.

2.  One can find a less resource intensive implementation of XFCE with the Linux Mint XFCE community edition.  EDIT:  (Just remembered that Mint XFCE CE is now a rolling release based on Debian, not Ubuntu per se.)

---

### Post by linuxyogi on 2011-07-27
[QUOTE=BrokenKingpin;11092581]
I still find Xubuntu to be a more complete package, and offers more  configuration utilities. It is not as fast as Lubuntu (but still quite  fast), but it feels like a more complete package.[/QUOTE

^ I agree.


LXDE still needs some tools related to the DE. Like menu editor, a screen capture tool & likewise. ATM user needs to install/ borrow tools from other DEs. Otherwise Lubuntu is awesome.

The latest XFCE (XFCE4) looks real ugly.

---

### Post by kerry_s on 2011-07-27
I use lubuntu as my main de

---

### Post by Rodney9 on 2011-07-27
> **MG&TL said:**
> It is insanely fast when compared to ubuntu, or even xubuntu. I have absolutely no idea why though. It looks awful, and customization is limited, but it is very usable, and is the fastest 'usable' OS I have installed.

I agree, very ugly.

---

### Post by HoKaze on 2011-07-27
I haven't tried Lubuntu out myself but I have tried LXDE before and for quite a while openbox on its own was my wm of choice. The DE is light, fast, has some good alternative applications, a pretty easy to use interface and installing heavier gtk apps usually doesn't pull in too many dependencies.
It's definitely a good distro if xfce is too bloated for you, you're using an old pc but want to use ubuntu rather than debian, etc.

---

### Post by vehemoth on 2011-07-28
I installed lxde fedora on my netbook and I found it amazingly fast and surprisingly not bad looking.

It would be nice to have a few more applications for configuring it but it's not too bad doing it in the files.
I would consider lubuntu but I have found the other versions of ubuntu to be overly bloated compared to other distros and I thought I would try rpm/yum for a change.

I do agree though that the other wm/de are underrated and are better than I had expected before trying them.

---

### Post by northwestuntu on 2011-07-29
ive used lubuntu before and liked it.  only problem was no 64 bit version.  im about to give peppermint os a shot since it has 64 bit edition.  

i also see linux mint is about to release a lxde version, but lol again no 64 version?  i understand these are for older systems, but they run great on newer systems also.  why limit people to 32?

really like how snappy the lxde/openbox systems are.  

i just don't care for all the extras going in to ubuntu.  i really have no need for them.  browser/music/video and that's all i need.

:popcorn:

---

### Post by phosphide on 2011-08-05
I'm even more limited than that. I just need a browser.

---

### Post by northwestuntu on 2011-08-05
> **phosphide said:**
> I'm even more limited than that. I just need a browser.


i think thats the case with most people.

---

### Post by linuxyogi on 2011-08-05
> **northwestuntu said:**
> ive used lubuntu before and liked it.  only problem was no 64 bit version.  im about to give peppermint os a shot since it has 64 bit edition.  

i also see linux mint is about to release a lxde version, but lol again no 64 version?  i understand these are for older systems, but they run great on newer systems also.  why limit people to 32?

really like how snappy the lxde/openbox systems are.  

i just don't care for all the extras going in to ubuntu.  i really have no need for them.  browser/music/video and that's all i need.

:popcorn:

Install the base using the 64 Bit Ubuntu Minimal Install CD. 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then install LXDE  [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by BrokenKingpin on 2011-08-05
> **drawkcab said:**
> 2 random observations:

1.  As Xubuntu bloats up, Lubuntu is filling in as needed.

2.  One can find a less resource intensive implementation of XFCE with the Linux Mint XFCE community edition.  EDIT:  (Just remembered that Mint XFCE CE is now a rolling release based on Debian, not Ubuntu per se.)

The Xubuntu team have been doing a lot of work to slim down the bloat. Xubuntu 11.04 removed a lot of Gnome dependencies, and 10.10 will continue to do so (removal of GDM is going to be awesome).

I would say that the Linux Mint Xfce Edition (Debian based) is far more bloated than Xubuntu is right now, and they are still on the old 4.6 version of Xfce. On top of that, it is horribly buggy. I love the concept of LMDE, but they have a lot of work to do if they want to compete with Ubuntu/Xubuntu.

My apologies for going off topic.

---

### Post by Swagman on 2011-08-05
> **northwestuntu said:**
> ive used lubuntu before and liked it.  only problem was no 64 bit version.  im about to give peppermint os a shot since it has 64 bit edition.  

i also see linux mint is about to release a lxde version, but lol again no 64 version?  i understand these are for older systems, but they run great on newer systems also.  why limit people to 32?

really like how snappy the lxde/openbox systems are.  

i just don't care for all the extras going in to ubuntu.  i really have no need for them.  browser/music/video and that's all i need.

:popcorn:



Peppermint 64 is blistering quick..

---

### Post by northwestuntu on 2011-08-06
> **Swagman said:**
> Peppermint 64 is blistering quick..

ya i got a new setup im building and very excited to see how fast it is :p

---

### Post by graabein on 2011-08-07
What's ugly about Lubuntu? Fonts, window borders, controls, panel? Or is it mainly the default theme?

If it is as easy as GNOME to use I might install it on my old box that my parents occasionally use. It's a bit old so the speed increase should be very welcome. They mainly use a web browser and a simple card game on it.

Is it faster running a modern browser (Firefox 5) than default Ubuntu on the same machine specs do you think?

Edit: Peppermint looks interesting. What is their release cycle (for updated packages and security updates)? They should modify the default window border. It looks sweet except for that old black glossy border with the tiny monochrome minimize/maximize/close buttons. Just to enhance their brand/look, you know?

---

### Post by Madspyman on 2011-08-07
I love Lubuntu, especially when compared to the uber branding and bloat that Ubuntu comes packaged with today. I usually install Ubuntu from a minimal CD and build my graphical experience around Openbox, so Lubuntu is my kind of distro from the get go. Not a big fan of the taskbar, but other than that it's my favorite Ubuntu based distro since Crunchbang 9.04.

---

### Post by XubuRoxMySox on 2011-08-07
> **Madspyman said:**
> I love Lubuntu, especially when compared to the uber branding and bloat that Ubuntu comes packaged with today. I usually install Ubuntu from a minimal CD and build my graphical experience around Openbox, so Lubuntu is my kind of distro from the get go. Not a big fan of the taskbar, but other than that it's my favorite Ubuntu based distro since Crunchbang 9.04.

I loved Crunchbang 9.04! It was awesome! I tried running LXDE on top of it and it was uber-buggy at the time, but back then LXDE was "under heavy development" (read: Beta). I toyed with U-Lite for a bit and it was equally buggy, but very speedy.

Since I discovered Xfce I haven't revisited LXDE, but I'm anxious to do so when I can afford to risk some breakage. I'm down to only one 'puter right now and it's "mission critical" so I just stick with Xubu Lucid. 

But alot of people have spent alot of time and alot of work to make Lubu a reality. Congratulations to the team for becoming "official" now!

-Robin

---

