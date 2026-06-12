---
title: "64bit, what a headache"
date: 2010-03-17
forum: Desktop Environments
---

### Post by RasterBurn on 2010-03-17
ok so i did the update today, and unfortunately guess what, it broke the desktop quite a familiar encounter with the last update, it seems that 64bit UBUNTU has more problems with my computer then i can put up with (although 32bit seems to run perfect on my wifes computer) does anyone else have these problems or am I the only one who seems to be encountering the problems? I would post the dmesg but unfortunately i cant get anywhere when booting up, get to the grub and then one kernel 19 will show the loading screen then black and thats the end of the story, kernel 20 doesnt even make it to the loading screen before it goes black, i have tried deleting the xorg.conf file and letting the xorg rebuild it but thats a no go, anyways, I am going back to 32bit UBUNTU as there seems to be far less problems with it, i would rather not fix my computer every time i install the updates.

---

### Post by hxcobd on 2010-03-17
Somewhat unrelated, but the linux administration job I start soon uses 64-bit CentOS. I'm not excited at all to work with it. (Love my 32-bit!)

I don't understand the logic behind anyone on linux moving to 64-bit. 

There's virtually no worthwhile performance boost, and you can actually add support for up to 64 gigs of RAM in 32-bit just by adding some REALLY simple boot-line parameters.

---

### Post by FunkyRes on 2010-03-17
I almost exclusively run 64-bit. I use Ubuntu and CentOS.

Dealing with any date beyond 2038 is one reason. But it is not the only reason. To see an example:

[http://www.domblogger.net/Calendar?y=2037&m=12](http://www.domblogger.net/Calendar?y=2037&m=12)

Click the link for January 2038 ...
Yes, there are solutions. The best solution though is to go 64 bit.

Exactly what problems are you experiencing?

For Java, the browser plugin can be a pain (in CentOS anyway), it used to work fine with iced-tea but now you have to install a non-free plugin. I do not use Java so that is not an issue for me.

For closed multimedia codecs like WMV and WMA, the fluendo codec packs works extremely well.

What exactly are the issues that is making it a headache for you?

For the kernel bug, I can't help you there, but it might help to post your hardware (chipset etc.)

---

### Post by RasterBurn on 2010-03-17
if you do alot of A/V related tasks such as video encoding then 64bit will do the tasks faster i use a program called DeVeDe and have noticed i can encode a dvd faster using a 64bit OS then i can using a 32bit OS (on the same machine of course) UBUNTU 8.10 64bit ran like a dream on my computer, but as soon as i upgraded to 9.10 the **** hit the fan, its been nothing but problems (not sure if 9.04 is effected cause i skipped 9.04) but i mean, i boot up 3/4 the time something on my desktop is wrong so i have to log out and back in to correct it, and then to get my desktop effects to work, again i have to log out and back in to get the setting to lock in (course that is a hopeless work around cause it never remembers the setting when you leave the session) and then updates, minor system updates work not a problem, new kernel versions on the other hand set me down with failing software like xorg or gnome, and when i do get them back up and running, i still have to reinstall my graphics driver so that 1280x720 renders correctly on my screen as well as my audio works, so total time wasted after a kernel upgrade, somewhere in the area of 1 - 2 hours trying to get things working again

---

### Post by FunkyRes on 2010-03-17
What is your video card?
I suspect that is where the issue is. Is it ATI?

I only buy nvidia cards because year after year after year there always seem to be people on every distro with ATI driver problems.

The proprietary nvidia driver works quite well for me and always has regardless of distro, though I never buy bleeding edge video cards, I'm not a gamer. And I always disable desktop effects, they annoy me.

With respect to 9.10 - I just did the upgrade and I think it was released prematurely, though none of my issues are due to it being 64-bit.

---

### Post by RasterBurn on 2010-03-17
well, lets as far as hardware goes, its AMD from a - z the machine is rigged for full HD video including blu-ray

```

michael@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 5GiB
     *-cpu
          product: AMD Phenom(tm) 9850 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
     *-pci:0
          description: Host bridge
          product: RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          resources: memory:0-1fffffff
        *-pci:0
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx0 port A)
             vendor: ATI Technologies Inc
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 ioport:a000(size=4096) memory:fe500000-fe5fffff ioport:c0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon HD 3870
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:c0000000-cfffffff(prefetchable) memory:fe5f0000-fe5fffff ioport:a000(size=256) memory:fe5c0000-fe5dffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Radeon HD 3870 Audio device
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fe5ec000-fe5effff
        *-pci:1
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port B)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:fe600000-fe7fffff
           *-multimedia
                description: Multimedia video controller
                product: CX23885 PCI Video and Audio Decoder
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=cx23885 latency=0
                resources: irq:17 memory:fe600000-fe7fffff
        *-pci:2
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port C)
             vendor: ATI Technologies Inc
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:27 ioport:b000(size=4096) memory:fe800000-fe8fffff
           *-network
                description: Ethernet interface
                product: 88E8056 PCI-E Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 12
                serial: 00:22:15:ed:03:e7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.0.102 latency=0 multicast=yes
                resources: irq:30 memory:fe8fc000-fe8fffff ioport:b800(size=256) memory:fe8c0000-fe8dffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: RD790 PCI to PCI bridge (PCI express gpp port D)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:28 ioport:c000(size=8192) memory:fe900000-fe9fffff
           *-ide
                description: IDE interface
                product: 88SE6121 SATA II Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: b2
                width: 32 bits
                clock: 33MHz
                capabilities: ide bus_master cap_list
                configuration: driver=pata_marvell latency=0
                resources: irq:19 ioport:d800(size=8) ioport:d400(size=4) ioport:d000(size=8) ioport:c800(size=4) ioport:c400(size=16) memory:fe9ffc00-fe9fffff
        *-pci:4
             description: PCI bridge
             product: RD790 PCI to PCI bridge (external gfx1 port A)
             vendor: ATI Technologies Inc
             physical id: b
             bus info: pci@0000:00:0b.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:29 ioport:e000(size=4096) memory:fea00000-feafffff ioport:d0000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Radeon HD 3870
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d0000000-dfffffff(prefetchable) memory:feaf0000-feafffff ioport:e000(size=256) memory:feac0000-feadffff(prefetchable)
           *-multimedia
                description: Audio device
                product: Radeon HD 3870 Audio device
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:16 memory:feaec000-feaeffff
        *-storage
             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage bus_master cap_list
             configuration: driver=ahci latency=64
             resources: irq:22 ioport:9000(size=8) ioport:8000(size=4) ioport:7000(size=8) ioport:6000(size=4) ioport:5000(size=16) memory:fe4ff800-fe4ffbff
        *-usb:0
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe4fe000-fe4fefff
        *-usb:1
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:16 memory:fe4fd000-fe4fdfff
        *-usb:2
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:17 memory:fe4ff000-fe4ff0ff
        *-usb:3
             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe4fc000-fe4fcfff
        *-usb:4
             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe4fb000-fe4fbfff
        *-usb:5
             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:fe4fa800-fe4fa8ff
        *-serial UNCLAIMED
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fe4f4000-fe4f7fff
        *-isa
             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:5
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:feb00000-febfffff
           *-network
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 6
                bus info: pci@0000:06:06.0
                logical name: wmaster0
                version: 01
                serial: 00:02:6f:4f:bc:c7
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:21 memory:febf0000-febfffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323
                vendor: Agere Systems
                physical id: 8
                bus info: pci@0000:06:08.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=24 mingnt=12
                resources: irq:22 memory:febef000-febeffff
        *-usb:6
             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
             resources: irq:18 memory:fe4f9000-fe4f9fff
     *-pci:1
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K10 [Opteron, Athlon64, Sempron] Link Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
  *-scsi
       physical id: 1
       bus info: scsi@8
       logical name: scsi8
       capabilities: scsi-host
       configuration: driver=usb-storage

```as you can see its all supported, it claims there is 5 gb memory but there is only 4gb with 1 gb swap, that is of course what the live cd is claiming due to the fact i cant get on without it. cant forget to mention that last week it decided it would be great to forget half the default aplications (aka what to do when a dvd movie is put in, or perhaps what program to play an mp3 with or an avi with), also if i install certain programs that just increases the chances that when i boot up my desktop will be wonky forcing me to log out and log back in (things like no desktop icons and no right click, no menu bar, perhaps no mouse cursor, you know the real stupid stuff that shouldn't occure, not to mention the error report app doesnt kick in to report that any errors have occured)

so i am thinking back to 32bit i go, perhaps they will have 64bit fixed and working properly by 2038 (about 28 years from now, i think there will be a new architecture to screw everything up by then :D)

---

### Post by FunkyRes on 2010-03-17
The 2038 issue also effects historic dates before 1902.
It's an issue for me as I work with records going back into the 19th century and have to use workarounds on my 32-bit system.

Hopefully the problem doesn't also exist in 32-bit. I think 9.10 is doing some new stuff with X11 that 9.04 and earlier did not do, that may be the cause.

---

### Post by RasterBurn on 2010-03-17
i dont know, right at this moment i am on the 32bit install disk, i now remember a couple more reasons why i dont care for the 32bit version (3gb ram instead of 3.9 i know the PAE extension fixes the cap 64GB on 32bit systems, wireless at ~9MBps instead of ~54, media encoding at half the speed it could be), 64bit didnt have the encoding and ram problem, the wireless wasnt perfect but it was closer to 54MBps, right now i am wondering if 64bit Debian would have more stable updates (in terms of kernel-image) or maybe just perform better then UBUNTU64 does, i mean 32bit UBUNTU runs like a dream on my wifes P4 machine with an ATI graphics card, absolutely no problems what so ever

---

### Post by RasterBurn on 2010-03-18
though no one could give me any insight to the fix i have figured it out and fixed it myself, too bad it was too simple to think of in the beginning, simply boot into a CLI using the recovery mode and re-install the ati driver (would be simpler if the kernel knew it was installed)

---

### Post by krazyd on 2010-03-18
> **RasterBurn said:**
> it seems that 64bit UBUNTU has more problems with my computer then i can put up with (although 32bit seems to run perfect on my wifes computer)

your issues are almost certainly hardware specific (different hardware between the two computers) and nothing to do with 64-bit.

glad to hear you figured it out. just wanted to mention that the open source radeon driver now supports 3D well enough for desktop effects, though it's still generally slower than proprietary for 3D gaming. Lucid should have it by default, and you can enable it in Karmic.

---

### Post by RasterBurn on 2010-03-18
well, i found due to my hardware setup (computer is pluged into a 42" HD LCD TV thru HDMI) with wireless keyboard and mouse i found that the default ati drivers that are installed on the computer when you install the OS choose 1280x720 resolution as the prefered, this is fine for me with the exception that the screen goes past the borders of the tv thus cutting off both the top and bottom menu, and i have a selection of that and 3 lower 4:3 aspect resolutions (1024x768, 800x600, 640x480, and maybe 720x480) all looking dull and washed out on my screen (i am sure you are familiar with running a low resolution on a high resolution tv or otherwise the quality of an older movie in a theater) anyways, i have tried installing the fglrx drivers from the repositories in the past with laptops running ati cards spending more time modifying the xserver config file to make the driver work right then doing anything else related to the driver :P bad experiences with them, but like i said in a previous post on this topic the drivers work great with the updates until its a new kernel version then everything goes to hell in terms of the desktop loading during bootup

---

### Post by nc_jed on 2010-03-31
> **RasterBurn said:**
> ... with the exception that the screen goes past the borders of the tv thus cutting off both the top and bottom menu...

I just did something similar with an older machine, HDMI cable and 42" TV and noticed the exact same thing.  I fixed mine through the TV and not the OS.  My Philips TV has a view mode or something and one of them fixes this issue.

Sorry I'm light on the details, but maybe it's another place to look.

- Jed

---

### Post by RasterBurn on 2010-03-31
my tv just wants to stretch everything with the other view modes so it was out of the question in terms of a fix :P

---

