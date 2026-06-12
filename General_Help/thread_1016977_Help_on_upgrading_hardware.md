---
title: "Help on upgrading hardware"
date: 2008-12-20
forum: General Help
---

### Post by japtar10101 on 2008-12-20
I know this isn't the correct place to ask, but I couldn't think of anywhere else.  I recently obtained a really old computer from the recycling center.  I wanted to turn this to a server for experimental reasons, using Xubuntu (sorry, still not a terminal expert).

I'm trying to upgrade this machine to a more formidable form.  I'm having a hard time recognizing, though, which hardware fits with this model.  I'm trying to figure out:
[LIST=1]
[*]Maximum memory size, how many, and what type.
[*]the best performing processor for this model.
[*]a PCI network card (ethernet) compatible with Linux.
[*]connection to harddrive.  For that matter, a harddrive bigger that 60 GB that is compatible with this model.
[/LIST]

Here's the specs:

Model name: E-machine T1090
[http://www2.shopping.com/xPF-E-Machines-T1090](http://www2.shopping.com/xPF-E-Machines-T1090)
[LIST]
[*]Intel Celeron Processor, 900Mhz.  Not sure of the actual processor name.  I couldn't get myself to remove the processor fan.
[*]It says on the cover, "128 MB memory", but Xubuntu told me there was "254 MB of memory left" when I couldn't get the BIOS configuration to install from CD.  Upon further inspection, there are 2 memory card slots, but the ones occupying it looked completely different from each other (one was marked 128 MB, but I couldn't figure out the other one).
[*]The pre-installed hard-drive is 20 GB.  It seems only one hard-drive can be installed securely, although If I can just leave another one hanging, I can probably connect another hard-drive to where the floppy disk is connected to.  the connections are definitely ribbons.
[*]Network connection is dial-up *shiver*.  There's 3 PCI ports, so I can insert an ethernet network card.
[/LIST]
Currently, Xubuntu is running fine on the computer, though slow.

Any examples from NewEgg.com will be great.

---

### Post by logos34 on 2008-12-21
It appears 256MB is the max ram supported.  So you might want to look for another 128MB stick to speed things up.

"Celeron" is the type of processor, but to find the exact model number here are some sommands:

> cat /proc/cpuinfo

sudo lshw 

The latter will give you WHOLE system info--disks, memory, everything.

Here's another which even outputs Bios info:

> sudo apt-get install dmidecode

sudo dmidecode

Any IDE hard disk will work, it will just be a tad slower (probably not even noticeable) since your storage controller only supports ata5/udma66.  Most IDE drives are now udma100.  You should have two IDE channels, supporting 2 devices on each ribbon cable (2 hard drives, cdrom and hard drive).  Yes, try to bolt it into the 3.5" floppy slot (don't leave it hanging.  Can't use floppy ribbon cable for hdd).  Make sure the jumper at the back of the hard disk is set correctly (just use 'cable select' and you should be fine). 

Look for cheapest 10/100 PCI ethernet card.  

I don't see any Bios update downloads:

[http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T1090](http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T1090)

hope that helps

---

### Post by japtar10101 on 2008-12-27
> **logos34 said:**
> It appears 256MB is the max ram supported.  So you might want to look for another 128MB stick to speed things up.

I found conflicting reports for that: a few websites say 512 MB (two 256 MB memory stick), while most says only up to 256 MB.  To be safe, I'm assuming 256 MB though (which it apparently has already, although I don't see why the report said "254 MB").

> **logos34 said:**
> Any IDE hard disk will work, it will just be a tad slower (probably not even noticeable) since your storage controller only supports ata5/udma66.  Most IDE drives are now udma100.  You should have two IDE channels, supporting 2 devices on each ribbon cable (2 hard drives, cdrom and hard drive).  Yes, try to bolt it into the 3.5" floppy slot (don't leave it hanging.  Can't use floppy ribbon cable for hdd).  Make sure the jumper at the back of the hard disk is set correctly (just use 'cable select' and you should be fine).

I'm not knowledgeable with electronics: is udma100 backward-compatible with udma66?  From your explanation, it sounds like it.

Thanks for the rest of the response.  I'll check on the processor later (just got back from vacation).

---

### Post by logos34 on 2008-12-27
> **japtar10101 said:**
> 
I'm not knowledgeable with electronics: is udma100 backward-compatible with udma66?  From your explanation, it sounds like it.

yes.

I have the reverse scenario: an old udma66 Quantum Fireball (4 GB) drive attached to a new computer.

---

### Post by polmir on 2008-12-27
**japtar10101**, type in terminal:```
lspci
```and post output.

---

### Post by japtar10101 on 2008-12-28
Bought a network card, so I can do things directly to this rusty machine.
> **polmir said:**
> ```
lspci
```
```

~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH (Graphics Memory Controller Hub) (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801AA AC'97 Modem Controller (rev 02)
01:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
> **logos34 said:**
> ```
cat /proc/cpuinfo

sudo lshw
```
```
~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 8
model name	: Celeron (Coppermine)
stepping	: 10
cpu MHz		: 897.310
cache size	: 128 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips	: 1796.31
clflush size	: 32

``````
~$ sudo lshw
PCI (sysfs)  
omiyat-server             
    description: Desktop Computer
    product: Emachines
    vendor: TriGem Computer, Inc.
    version: 100
    serial: 0000000000
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: administrator_password=enabled boot=oem-specific chassis=desktop cpus=1 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled
  *-core
       description: Motherboard
       product: TriGem System Board
       vendor: TriGem Computer, Inc.
       physical id: 0
       version: 000000
       serial: 000000000000000000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: Ver 5.02 (10/17/2001)
          size: 99KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppynec int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.10
          slot: U1
          size: 900MHz
          width: 32 bits
          clock: 100MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KiB
             capacity: 512KiB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: 1e
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 128MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 128MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 82810 GMCH (Graphics Memory Controller Hub)
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display
             description: VGA compatible controller
             product: 82810 (CGC) Chipset Graphics Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
        *-pci
             description: PCI bridge
             product: 82801AA PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: e
                bus info: pci@0000:01:0e.0
                logical name: eth0
                version: 10
                serial: 00:1e:2a:ba:45:f1
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.46 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801AA ISA Bridge (LPC)
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
             product: 82801AA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST320410A
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.34
                serial: 5FG0W8BP
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ee08ee08
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 73c14ef3-0a2b-4e39-a44a-b62b24f956bc
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-19 15:58:37 filesystem=ext3 modified=2008-12-28 12:54:49 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-12-28 12:54:49 state=mounted
              *-volume:1
                   description: Linux swap volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 1
                   serial: ef11b1f6-9a11-4727-9741-910c15f46482
                   size: 4769MiB
                   capacity: 4769MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-R/RW 48X16
                vendor: ATAPI
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 9.EK
                serial: ATAPI   CD-R/RW 48X16   9.EK
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted
        *-usb
             description: USB Controller
             product: 82801AA USB Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: 82801AA AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801AA AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0

```

---

### Post by polmir on 2008-12-28
Calm down, you can install Ubuntu.
RAM can be purchased very cheaply or receive as gifts from friends :)

---

### Post by japtar10101 on 2008-12-28
> **polmir said:**
> Calm down, you can install Ubuntu.
RAM can be purchased very cheaply or receive as gifts from friends :)

I'm running Xubuntu on it, and it's annoyingly slow...although I know it's only because it's old.

Speaking of RAM, is the maximum RAM for this machine 512 MB or only 256 MB?

---

### Post by polmir on 2008-12-28
> **japtar10101 said:**
> I know it's only because it's old.
Speaking of RAM, is the maximum RAM for this machine 512 MB or only 256 MB?
To simply browse the Internet and as a typewriter and even at that you can watch movies.

I have a similar computer with PIII 450, 512RAM and Debian Lenny with Gnome and often use it to browse the Internet and experiments.

Also installed Ubuntu on it not once.

---

### Post by japtar10101 on 2008-12-29
> **polmir said:**
> To simply browse the Internet and as a typewriter and even at that you can watch movies.

I have a similar computer with PIII 450, 512RAM and Debian Lenny with Gnome and often use it to browse the Internet and experiments.

Also installed Ubuntu on it not once.

So 512 MB is possible?  If so, in what connection type (I'm only familiar with DDR and DDR2)?

On an additional note, I find it disturbing I can't find more information on *which* Trigem Motherboard the system has...

EDIT: Bah, Google finally got me something useful -> [http://www.sysopt.com/forum/showthread.php?t=191701](http://www.sysopt.com/forum/showthread.php?t=191701)
I don't get this tech-talk, though.  Someone help me.

---

### Post by polmir on 2008-12-29
[URL="http://forum.worldstart.com/showthread.php?t=58289"]	
Read these comments[/URL]

---

### Post by CatKiller on 2008-12-29
Crucial has a great tool for seeing what memory is compatible with a given computer. They do it to make it easier to buy from them (which I've done in the past with no problems) although you don't have to; you can just take the information they give you to buy from another supplier.

[This]("http://www.crucial.com/store/listparts.aspx?model=T1090") is the page for the eMachines T1090. They say that 2×256MiB of PC133 is the maximum. PC133 can be comparatively quite expensive, since it isn't made any more and so is quite hard to get hold of. There did also used to be restrictions on the arrangements of the chips that were compatible with given older motherboards; some of them couldn't address all of the larger chips, and so it was necessary to find memory modules that had more smaller chips ("low-density"). It's actually PC100 that's sufficient for that computer (100 MHz Front-Side Bus) but that's even harder to acquire than PC133. They are backwards-compatible, though.

Thankfully memory configuration has become (a little) easier with modern computers.

---

### Post by japtar10101 on 2008-12-29
> **CatKiller said:**
> Crucial has a great tool for seeing what memory is compatible with a given computer. They do it to make it easier to buy from them (which I've done in the past with no problems) although you don't have to; you can just take the information they give you to buy from another supplier.

[This]("http://www.crucial.com/store/listparts.aspx?model=T1090") is the page for the eMachines T1090. They say that 2×256MiB of PC133 is the maximum. PC133 can be comparatively quite expensive, since it isn't made any more and so is quite hard to get hold of. There did also used to be restrictions on the arrangements of the chips that were compatible with given older motherboards; some of them couldn't address all of the larger chips, and so it was necessary to find memory modules that had more smaller chips ("low-density"). It's actually PC100 that's sufficient for that computer (100 MHz Front-Side Bus) but that's even harder to acquire than PC133. They are backwards-compatible, though.

Thankfully memory configuration has become (a little) easier with modern computers.

Do I have to install the 64 Bit version of xubuntu for the memory cards the website listed to be fully utilized, then?

EDIT: just checked Newegg.com.  Would these 2 products work:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820136009](http://www.newegg.com/Product/Product.aspx?Item=N82E16820136009)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820146303](http://www.newegg.com/Product/Product.aspx?Item=N82E16820146303)
I'm suspicious about the cheaper one (bottom)...

EDIT #2: These are still cheaper than my 1 GB memory cards for another desktop.

---

### Post by polmir on 2008-12-29
> **japtar10101 said:**
> Do I have to install the 64 Bit version of xubuntu for the memory cards the website listed to be fully utilized, then?
No, you can install only versions 32 Bit system.

---

### Post by CatKiller on 2008-12-29
> **japtar10101 said:**
> Do I have to install the 64 Bit version of xubuntu for the memory cards the website listed to be fully utilized, then?

EDIT: just checked Newegg.com.  Would these 2 products work:

You don't need to install the 64-bit version if you aren't using a 64-bit processor. Which you aren't. The warning about the limits of 32-bit memory addressing is for addressing more than 4GiB of memory. Which you aren't.

Kingston is one of the premier brands of RAM, but Mushkin is fine too. Either should work fine, provided the chip density is correct. Some older motherboards only understood how to address low-density chips, meaning that if you put high-density chips in them the memory controller would only see half of the memory in each chip, leading to only seeing half of the memory in the whole module. That's what the 32M×16 style numbers refer to. I have no idea at this point whether the memory controller on that motherboard needs low-density chips or not, and the comments on those NewEgg pages suggest that you can't tell before you get them whether you're going to get low-density or high-density chips from them anyway. If you put them in and only see half the memory from each module, then that's the cause. Most sites have a reasonable returns policy if the product isn't compatible, but it's still time that the computer isn't upgraded. It might not turn out to be an issue at all, but it is a risk with that technology.

---

### Post by japtar10101 on 2009-01-01
Hey, thanks for the information.  My wallet is a little tight right now, but I'll definitely keep this thread as reference.

I have bumped into a problem, however, that baffles me.  I attempted to make my network IP address static by editting */etc/network/interfaces* to below:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
    address 192.168.0.121
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

```

Note: the file originally said:
```

auto lo
iface lo inet loopback

```

When I do this, I cannot connect to the internet.  Change the settings back to roaming on NMapplet, and everything returns back to normal.

What may be the cause of this?  Does it have to do with the network service that we have?  Is it a network card issue?  Or is it simply because my computer is old?

Thanks again.

---

### Post by CatKiller on 2009-01-02
> **japtar10101 said:**
> I attempted to make my network IP address static by editting */etc/network/interfaces* to below:

I don't know much about networking - you're probably best off asking particulars in the Networking & Wireless sub-forum to get a more knowledgeable response. I believe it's changed somewhat recently with the new NetworkManager, but I don't really know how.

---

