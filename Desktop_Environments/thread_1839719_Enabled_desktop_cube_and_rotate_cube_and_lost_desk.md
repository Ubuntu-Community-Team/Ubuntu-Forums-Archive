---
title: "Enabled desktop cube and rotate cube and lost desktop functionality"
date: 2011-09-06
forum: Desktop Environments
---

### Post by GumpTron on 2011-09-06
I feel like a grade A noob but here it goes... :popcorn:


I went into the Compiz settings panel and I wanted to enable the 3d rotating cube. I enabled both functions which meant I had to disable two things, I am pretty sure one was the sidebar program that holds icons. I rebooted and now all I can do is see the right click menu and that's it. I can't see the top bar or the side bar and I can't do anything. Is there a way to solve this? :guitar:

---

### Post by nothingspecial on 2011-09-06
I nearly warned you against doing that, I should have #-o

First thing to try, Press Ctrl-Alt-T

hopefully a terminal will appear

type

```
unity --reset
```

If that doesn't work, try typing

```
compizconfig-settings-manager
```

and undoing the changes you made.

I think you have to enable desktop wall and unity plugin (and disable the cube)

---

### Post by GumpTron on 2011-09-06
terminal will not open :(

I am able to right click and create folders. Is there a way to get to terminal by right clicking as a starting point?

---

### Post by nothingspecial on 2011-09-06
Ok in that case Press Ctrl-Alt-F1

This will get you to TTY1, you will have to log in and type your password. You won't see it being typed but just type it and press enter. Then type

```
unity --reset
```

followed by

```
sudo service gdm restart
```

you'll have to tpe your password again which you won't see.

Hopefully that should do the trick.

---

### Post by GumpTron on 2011-09-06
I restarted the notebook and for some reason everything went back to normal and I cant explain it. I simply rebooted the third or fourth time and everything is back to normal. I will keep your advice on record though haha. Thank you for your help :guitar:

---

### Post by wildmanne39 on 2011-09-06
Hi, you can click on how to set up the cube in 11.04 in my signature below this text and follow the guide it has pictures for every step.
Thank you

---

### Post by GumpTron on 2011-09-06
thanks :o

---

### Post by wildmanne39 on 2011-09-06
Hi, your welcome!

---

### Post by digrejzo on 2011-09-06
sorry for somewhat hijacking the thread, but I can't seem to find the appropriate topic for this kind of problem and if I'm not mistaken, the compiz forums are spammed hard these days.

I managed to disable unity and turn on cube/compiz in general, and everything works fine. I also got the Dust theme, and theres a little thing I can't figure out. 
how do I remove these lines (see the attached screenshot) on both sides of every window?
I have the feeling window decoration plugin does that, but can't seem to find what creates the "shadow" if that's what it is. any help on the matter would be highly appreciated =)

thanks guys!

---

### Post by wildmanne39 on 2011-09-06
Hi welome to the forum! I am not sure but when you say you disabled unity it that to set up compiz then you reenabled it or are you using claissic mode?

Did you use the guide in my link?
Thank you

---

### Post by digrejzo on 2011-09-07
oh yeah, forgot to tell you that.
nope, I didn't follow the guide, but I did pretty much all you mentioned, and yeah, I'm using ubuntu classic mode. 
using natty, if that helps.


thanks again =)

---

### Post by wildmanne39 on 2011-09-07
Hi, in classic mode there is a issue with compiz I am not sure it is the cause of your problem but here is a link for it.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
Thank you

---

### Post by digrejzo on 2011-09-07
downgraded, the problem is still there. it's not that much of a big deal, but I kinda wanted to have that simple and clean window look I had back on 8.04.

if a solution comes up, I'll be glad to share it with you guys. =)

---

### Post by wildmanne39 on 2011-09-07
Hi, post the results of these commands here please:
```
sudo lshw
```
```
/usr/lib/nux/unity_support_test -p
```
```
dmesg | grep video
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by digrejzo on 2011-09-07
```
    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=00000000-0000-0000-0000-001FD09D439C
  *-core
       description: Motherboard
       product: EP45-UD3
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F3
          date: 09/18/2008
          size: 128KiB
          capacity: 960KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: Socket 775
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 266MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=0
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
             size: 3MiB
             capabilities: synchronous internal write-back
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
          physical id: 19
          slot: System board or motherboard
          size: 1GiB
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
             description: DIMM [empty]
             physical id: 3
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 2133MHz
          capacity: 2133MHz
          capabilities: ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 4 Series Chipset DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 4 Series Chipset PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:b000(size=4096) memory:e4000000-e7ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G92 [GeForce 9600 GSO]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e6000000-e6ffffff memory:d0000000-dfffffff memory:e4000000-e5ffffff ioport:b000(size=128) memory:e7000000-e701ffff
        *-usb:0
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e100(size=32)
        *-usb:1
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:e200(size=32)
        *-usb:2
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e000(size=32)
        *-usb:3
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:e9305000-e93053ff
        *-multimedia
             description: Audio device
             product: 82801JI (ICH10 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:45 memory:e9300000-e9303fff
        *-pci:1
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:3ff00000-400fffff ioport:40100000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:c000(size=4096) memory:e9000000-e90fffff ioport:40300000(size=2097152)
           *-storage
                description: SATA controller
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm pciexpress ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:19 memory:e9000000-e9001fff
           *-ide
                description: IDE interface
                product: JMB362/JMB363 Serial ATA Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                logical name: scsi4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ide pm bus_master cap_list emulated
                configuration: driver=pata_jmicron latency=0
                resources: irq:16 ioport:c000(size=8) ioport:c100(size=4) ioport:c200(size=8) ioport:c300(size=4) ioport:c400(size=16)
              *-cdrom
                   description: DVD-RAM writer
                   product: DVD-RAM GH22NP20
                   vendor: HL-DT-ST
                   physical id: 0.1.0
                   bus info: scsi@4:0.1.0
                   logical name: /dev/cdrom
                   logical name: /dev/cdrw
                   logical name: /dev/dvd
                   logical name: /dev/dvdrw
                   logical name: /dev/scd0
                   logical name: /dev/sr0
                   version: 1.02
                   capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: ansiversion=5 status=nodisc
        *-pci:3
             description: PCI bridge
             product: 82801JI (ICH10 Family) PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:d000(size=4096) memory:e8000000-e8ffffff ioport:e9100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:d0:9d:43:9c
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:44 ioport:d000(size=256) memory:e9110000-e9110fff memory:e9100000-e910ffff memory:e9120000-e912ffff
        *-usb:4
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e300(size=32)
        *-usb:5
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e400(size=32)
        *-usb:6
             description: USB Controller
             product: 82801JI (ICH10 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e500(size=32)
        *-usb:7
             description: USB Controller
             product: 82801JI (ICH10 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e9304000-e93043ff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 90
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: memory:e9200000-e92fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:05:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:23 memory:e9204000-e92047ff memory:e9200000-e9203fff
        *-isa
             description: ISA bridge
             product: 82801JIB (ICH10) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) ioport:f100(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD3200AAKS-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WCAT14336619
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=20f520f5
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /media/System
                   version: 3.1
                   serial: dcd6f2f4-910c-5548-b0e6-47de1c52b299
                   size: 87GiB
                   capacity: 87GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2009-11-30 05:45:11 filesystem=ntfs label=System mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 205GiB
                   capacity: 205GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: HPFS/NTFS partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /media/Musica
                      capacity: 97GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:1
                      description: HPFS/NTFS partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /media/Applications
                      capacity: 102GiB
                      configuration: mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1000MiB
                      capabilities: nofs
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home
                      capacity: 4143MiB
                      configuration: mount.fstype=ext3 mount.options=rw,relatime,errors=continue,commit=5,barrier=0,data=ordered state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /
                   version: 1.0
                   serial: 63e32549-9f24-4404-bd45-b3834855e72e
                   size: 5002MiB
                   capacity: 5002MiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2011-09-06 02:07:36 filesystem=ext3 modified=2011-09-06 02:21:58 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,commit=5,barrier=0,data=ordered mounted=2011-09-07 19:28:06 state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e9306000-e93060ff ioport:500(size=32)
        *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:e700(size=8) ioport:e800(size=4) ioport:e900(size=8) ioport:ea00(size=4) ioport:eb00(size=16) ioport:ec00(size=16)

``````
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9600 GSO/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

``````
digrejzo@deGzyrx:~$ dmesg | grep video
[    0.241801] pci 0000:01:00.0: Boot video device

```

these are the outputs I get, but nothing rings a bell here, unfortunately =(

---

### Post by wildmanne39 on 2011-09-07
Hi, post the results of this command please:
```
cat /var/log/Xorg.0.log
```
Also how did you install the nvidia driver?
Thank you

---

### Post by mc4man on 2011-09-07
> **digrejzo said:**
> sorry for somewhat hijacking the thread, but I can't seem to find the appropriate topic for this kind of problem and if I'm not mistaken, the compiz forums are spammed hard these days.

I managed to disable unity and turn on cube/compiz in general, and everything works fine. I also got the Dust theme, and theres a little thing I can't figure out. 
how do I remove these lines (see the attached screenshot) on both sides of every window?
I have the feeling window decoration plugin does that, but can't seem to find what creates the "shadow" if that's what it is. any help on the matter would be highly appreciated =)

thanks guys!
The borders shown may be the default ones for dust (don't use here
Mainly using 11.10 now but as I remember you can download the 'dust extras', add to your themes and then change to 'dust borderless' in the 'window border' section of Customize theme as shown in screen

See here in Download section (also tells how to install
[https://wiki.ubuntu.com/Artwork/Incoming/DustTheme](https://wiki.ubuntu.com/Artwork/Incoming/DustTheme)

The link on above page takes you here - you want dust-extras
[https://launchpad.net/dusttheme/0.5/0.5.0](https://launchpad.net/dusttheme/0.5/0.5.0)

---

### Post by digrejzo on 2011-09-08
thanks a bunch guys, it works. I forgot to mess around with the customization, I would've figured it out myself without all the hassle =)

thanks again, cheers!
:popcorn:

---

### Post by wildmanne39 on 2011-09-08
Hi, I am glad you got it fixed, enjoy ubuntu.

---

