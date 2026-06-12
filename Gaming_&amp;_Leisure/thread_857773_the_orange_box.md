---
title: "the orange box"
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by 1467 on 2008-07-12
i installed it no problems but if i try to play i get this  your hardware must suport at least pixel shader 1.1 to run the game 

is their any thing i can do about that ?

---

### Post by ChameleonDave on 2008-07-12
> **1467 said:**
> i installed it no problems but if i try to play i get this  your hardware must suport at least pixel shader 1.1 to run the game 

is their any thing i can do about that ?
You haven't really said what you are talking about.  More information please.

---

### Post by 1467 on 2008-07-12
i dont have any more

---

### Post by 1467 on 2008-07-12
i get this [ATTACH]77550[/ATTACH]

---

### Post by YaroMan86 on 2008-07-12
> **1467 said:**
> i get this [ATTACH]77550[/ATTACH]

Do you have the best drivers available installed for your video card?

---

### Post by 1467 on 2008-07-12
how do i know if i do ?

---

### Post by 1467 on 2008-07-12
hl2 works good but not any of the the others

---

### Post by YaroMan86 on 2008-07-12
Can you tell me what video card you use?

---

### Post by 1467 on 2008-07-12
how do i tell 
its a nvidia thats all i know

---

### Post by ChameleonDave on 2008-07-13
> **1467 said:**
> i dont have any more
<Sigh>

OK, I've looked it up, and the [Orange Box]("http://en.wikipedia.org/wiki/The_Orange_Box") is a compilation of games for the XBox 360, PlayStation 3 and MS Windows.  You are presumably trying to run this software through [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29").  There is a [separate forum for Wine]("http://ubuntuforums.org/forumdisplay.php?f=31"), I believe.

If you don't know what hardware you have, then open a [terminal]("https://help.ubuntu.com/8.04/basic-commands/C/starting-terminal.html") and enter the following commands each on their own line:

```

sudo lshw

uname -a

cat /etc/lsb-release

```Copy and paste the output here, using the "#" button in the forum editor.

---

### Post by 1467 on 2008-07-13
linux-box                 
    description: Mini Tower Computer
    product: Dimension 4550
    vendor: Dell Computer Corporation
    serial: 4PK9Z11
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=44454C4C-5000-104B-8039-B4C04F5A3131
  *-core
       description: Motherboard
       vendor: Dell Computer Corp.
       physical id: 0
       serial: ..              .
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A01 (09/17/2002)
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
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
             size: 512KiB
             capacity: 512KiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GiB
          capacity: 1GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 01
             width: 32 bits
             clock: 66MHz
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
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: 10
                serial: 00:08:a1:5d:4f:df
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax/Voice/Spkp Modem
                vendor: Conexant
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-multimedia
                description: Multimedia controller
                product: SAA7130 Video Broadcast Decoder
                vendor: Philips Semiconductors
                physical id: 2
                bus info: pci@0000:02:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=saa7134 latency=64 maxlatency=32 mingnt=84 module=saa7134
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 81
                serial: 00:07:e9:a8:bf:43
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
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
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk:0
                description: ATA Disk
                product: Maxtor 6E030L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: NAR6
                serial: E175AR2E
                size: 28GiB (30GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=6ada6ada
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 28191960-95b1-4aa7-a120-9cc125d706b4
                   size: 9538MiB
                   capacity: 9538MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-19 14:44:23 filesystem=ext3 modified=2008-07-12 23:57:14 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-07-12 23:57:14 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /home
                   version: 1.0
                   serial: 58475306-bd9e-47c9-a3c8-44da5a515019
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-19 14:44:31 filesystem=ext3 modified=2008-07-12 23:57:15 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-07-12 23:57:15 state=mounted
           *-disk:1
                description: ATA Disk
                product: MAXTOR 6L040J2
                vendor: Maxtor
                physical id: 1
                bus info: scsi@0:0.1.0
                logical name: /dev/sdb
                version: A93.
                serial: 662224415990
                size: 37GiB (40GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=fd478bc7
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.1.0,1
                   logical name: /dev/sdb1
                   version: 1.0
                   serial: ef71b05f-5e4d-49b3-a13a-c12d1ce85f4f
                   size: 9538MiB
                   capacity: 37GiB
                   capabilities: primary extended partitioned partitioned:extended journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-06-19 13:56:34 filesystem=ext3 modified=2008-06-19 14:09:25 mounted=2008-06-19 13:56:59 state=clean
                 *-logicalvolume
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 37GiB
           *-cdrom:0
                description: DVD reader
                product: DVD-ROM SD-616T
                vendor: SAMSUNG
                physical id: 2
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: F308
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open
           *-cdrom:1
                description: CD-R/CD-RW writer
                product: CD-R/RW SW-240B
                vendor: SAMSUNG
                physical id: 3
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom1
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: BD11
                serial: [SAMSUNG CD-R/RW SW-240B BD11D
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0

---

### Post by 1467 on 2008-07-13
nate@linux-box:~$ uname -a
Linux linux-box 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
nate@linux-box:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
nate@linux-box:~$

---

### Post by ChameleonDave on 2008-07-13
You have an [NVidia GeForce4 MX 420]("http://www.nvidia.com/page/geforce4mx.html") &#8212; rather an old model, not suitable for serious gaming.

Here is a page detailing some problems with your video card:

[http://en.wikipedia.org/wiki/GeForce_4_Series#Known_problems](http://en.wikipedia.org/wiki/GeForce_4_Series#Known_problems)

---

### Post by 1467 on 2008-07-13
so i need 2 buy a new one 2 play right ?

---

### Post by 1467 on 2008-07-13
how do i know if it will work

---

### Post by 1467 on 2008-07-13
will this 1 work ok? 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R")

---

### Post by ChameleonDave on 2008-07-13
> **1467 said:**
> so i need 2 buy a new one 2 play right ?
Well, firstly, the site I linked to mentions that pixel-shader support can be enabled by using the right drivers.  That sound like the first obvious thing to try.

Secondly, yes, even if you get it working, I doubt you will have a satisfying experience with a graphics card from 2002.

> **1467 said:**
> how do i know if it will work
Nothing is certain in life, [except death and taxes]("http://en.wikiquote.org/wiki/Benjamin_Franklin").

However, since you are apparently running this via Wine, the first logical place to check to see if this game is likely to work is the [Wine application database]("http://appdb.winehq.org/").

Remember that only Linux programs can be expected to work with Linux.  If a Windows game works, it's a lucky bonus, not something to expect as a matter of course.

---

### Post by ChameleonDave on 2008-07-13
> **1467 said:**
> will this 1 work ok? 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R)

Probably.  Looks OK.   Search these forums to see if anyone has mentioned it as a good or bad one.

Also try [http://linuxhardware.org](http://linuxhardware.org).  They have a growing database of stuff that works or doesn't work.

I personally have an NVidia GeForce 7900 GS.

---

### Post by mister_k81 on 2008-07-13
> **1467 said:**
> will this 1 work ok? 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127273R")

You might want to make sure that your motherboard has a PCI Express slot before buying another card. With a graphics card that old, you might still be using AGP.

---

### Post by ChameleonDave on 2008-07-13
> **mister_k81 said:**
> You might want to make sure that your motherboard has a PCI Express slot before buying another card. With a graphics card that old, you might still be using AGP.

Indeed.  He is using a [Dell]("http://dell.com") [Dimension]("http://pcworld.about.com/news/Oct242002id106316.htm") [4550]("http://reviews.cnet.com/desktops/dell-dimension-4550-pentium/4514-3118_7-20478986.html"), with four [PCI]("http://en.wikipedia.org/wiki/Peripheral_Component_Interconnect") slots and one 4x [AGP]("http://en.wikipedia.org/wiki/AGP") slot.  It's not even fully compatible with 8x AGP cards.  It has no [PCI Express]("http://en.wikipedia.org/wiki/PCI_Express") slot.

The [GeForce 7300LE]("http://www.nvidia.com/page/geforce_7300.html") that he was looking at requires x16 PCI Express.  :-(

---

### Post by 1467 on 2008-07-14
oh well ty vary much for your help

---

### Post by 1467 on 2008-07-14
where do i get versions 53.

---

### Post by ChameleonDave on 2008-07-14
> **1467 said:**
> where do i get versions 53.
I fear that the "53.xx" version drivers mentioned in the Wikipedia article refer to Windows drivers.  I don't know if that would correspond to something in the Linux drivers or not.  I myself would simply assume that the normal drivers are doing a good enough job.  You might have to do a bit of hacking, compiling old drivers by yourself, if you want to squeeze more performance out of your ageing card.  It's something you'd have to look into by yourself.

I just don't think you can expect to get much gaming done on such an old box, especially not via Wine.  Either use different hardware or play simpler games.

---

### Post by 1467 on 2008-07-14
do u think i can find one under $60

---

