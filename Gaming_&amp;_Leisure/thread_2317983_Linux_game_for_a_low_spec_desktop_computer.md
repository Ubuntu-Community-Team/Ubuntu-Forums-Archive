---
title: "Linux game for a low spec desktop computer"
date: 2016-03-22
forum: Gaming &amp; Leisure
---

### Post by BadassRare on 2016-03-22
This may not sound very low spec for a computer but I am looking for games that work on ubuntu linux 12.04. I don't have the full specs but however i do know that this does not have pixel shader 2.0 because of minecrafts warning back when it was going through the big update and its missing the proper open gl to run steam because of the white boxes that you can not see through. i only have about a 1 gb to work with for ram but due to something useing a few megabytes i have 999 (exactly believe it or not) megabytes of Ram to work with and firefox uses a great deal of it. The computer itself is a dell optiplex 260 made back in 2001 or 2002 when windows xp came out. any help is greatly appreciated and i don't have much hard drive space to work with. 80gbs which is less now for what i have already downloaded plus what Linux itself is using.

---

### Post by mörgæs on 2016-03-22
Hi, welcome to the fora.

I also have an Optiplex 260 (among other Dells) and from birth it has a weak graphics processor. Unless you have added a stronger one I think your chances are low.

If you are into gaming have you considered buying a (say) 4-6 years old used rig?

---

### Post by BadassRare on 2016-03-22
Well if i had the money believe me i would absolutely love too, however things are rough right now and i have like 2 laptops with a broke screen and one hp that is litterally falling apart. so im stuck with this old things...as for the graphics processer im trying to remember the terminal command to bring all that up which if i can find i will post but i do believe its a quad core (i think)

> **BadassRare said:**
> Well if i had the money believe me i would absolutely love too, however things are rough right now and i have like 2 laptops with a broke screen and one hp that is litterally falling apart. so im stuck with this old things...as for the graphics processer im trying to remember the terminal command to bring all that up which if i can find i will post but i do believe its a quad core (i think)

processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Pentium(R) 4 CPU 2.40GHz

---

### Post by mastablasta on 2016-03-22
```
sudo lshw **-sanitize**
```

will display the hardware. you can copy the output and paste it here. or you can install hardinfo which can generate an HTML report you can then attach here.

hard to say what will run exactly. but definitely old DOS games. depending on the GPU you may be able to run Quake3 based games. if so then there are a few that are nice ones that can run in wine. would really need to see the CPU and GPU first.

furthermore default Ubutnu 14.04 interface might be quite heavy for your system. so you may benefit from moving to Xubutnu or Lubuntu or Mate. And keep Firefox off while playing games to free up RAM.

what type of games are you interested in playing? RPG, FPS, turn based strategy, real time strategy, fighting games, shoot em up, arcade, racing?!

---

### Post by BadassRare on 2016-03-22
> **mastablasta said:**
> ```
sudo lshw **-sanitize**
```

will display the hardware. you can copy the output and paste it here. or you can install hardinfo which can generate an HTML report you can then attach here.

hard to say what will run exactly. but definitely old DOS games. depending on the GPU you may be able to run Quake3 based games. if so then there are a few that are nice ones that can run in wine. would really need to see the CPU and GPU first.

furthermore default Ubutnu 14.04 interface might be quite heavy for your system. so you may benefit from moving to Xubutnu or Lubuntu or Mate. And keep Firefox off while playing games to free up RAM.

what type of games are you interested in playing? RPG, FPS, turn based strategy, real time strategy, fighting games, shoot em up, arcade, racing?!

```
computer                  
    description: Mini Tower Computer
    product: OptiPlex GX260
    vendor: Winbond Electronics
    serial: [REMOVED]
    width: 32 bits
    capabilities: smp-1.4 smp
    configuration: administrator_password=enabled boot=normal chassis=mini-tower cpus=1 power-on_password=enabled uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 02X378
       vendor: Winbond Electronics
       physical id: 0
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A09
          date: 11/01/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.7
          slot: Microprocessor
          size: 2400MHz
          capacity: 3060MHz
          width: 32 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 16KiB
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
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:f0000000-f7ffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:ff680000-ff6fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ffa00800-ffa00bff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=4096) memory:ff800000-ff9fffff
           *-network:0
                description: Ethernet interface
                product: 3CR990-TX-97 [Typhoon 168-bit]
                vendor: 3Com Corporation
                physical id: 7
                bus info: pci@0000:01:07.0
                logical name: eth1
                version: 02
                serial: [REMOVED]
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=typhoon duplex=half firmware=03.001.008 latency=64 link=no maxlatency=5 mingnt=10 multicast=yes port=twisted pair speed=10Mbit/s
                resources: irq:16 ioport:ec80(size=128) memory:ff8c0000-ff8fffff
           *-network:1
                description: Ethernet interface
                product: 82540EM Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 02
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=[REMOVED] latency=64 link=yes mingnt=255 multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:18 memory:ff8a0000-ff8bffff ioport:ec40(size=64)
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
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:40000000-400003ff
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
             resources: ioport:dc80(size=32)
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
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:d800(size=256) ioport:dc40(size=64) memory:ffa00400-ffa005ff memory:ffa00000-ffa000ff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST380023A
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.33
             serial: [REMOVED]
             size: 74GiB (80GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000d1d7c
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 73GiB
                capacity: 73GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-03-03 07:03:37 filesystem=ext4 lastmountpoint=/ modified=2016-03-03 07:21:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-03-21 14:56:11 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1021MiB
                capacity: 1021MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1021MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: SCSI CD-ROM
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio
             configuration: status=nodisc
```


Im into about everything...tho fps and fnaf like games always hit home and rpgs do good too...basiccly anything just no raceing

Edit: i tried to do wine for games like "One night at flumptys" and "The Darkest Worlds" and i got a error for both...and i tried one for a old game i played back on 9.04 when it was still good and it worked but now it won't sadly tho i think i used the linux install with it...but i don't remember for that was so long ago. I also love horror games

---

### Post by Alex_Moonshine on 2016-03-22
I don't think your computer can manage anything with any kind of graphics that was made in the last 3-5 years. There are, however, roguelikes like Dungeon Crawl, ADOM, Nethack, etc., that will run of anything and can provide 100s of hours of gameplay, if you are into that thing. Tales of Maj'Eyal is one of the newer ones. Also check out [Nuclear Throne]("http://store.steampowered.com/app/242680/"), it may or may not run for you. You can also probably run stuff like Fallout 1-2, Planescape, Master of Orion 1-2, etc. in wine. I'm not much of FPS guy, but Doom should run in dosbox :)

---

### Post by BadassRare on 2016-03-22
it can handle a few rpg maker games that was made recently and on wine supriseingly. It can handle emulator games up to snes which is nice. I do appricate the suggestions very much, but i failed to mention that im on a free game binge like gamejolt horror games and anywhere else i can find them. I figured out what was wrong with that one game i tried in wine which did have a linux distribution but stupid me didn't think to look in the right spot. Although i notied some graphical errors with it which i believe might be because it was made in unity and with my graphics...yea dosn't suprise me. im downloading Swamp Sim which i saw Markiplier play awhile back so im hopeing i may get lucky. since i do like the slender games a little bit. As for doom, well i kinda beat that game into the ground and back again. Thank you so much for all the suggestions tho and if any of those are free and such please do provide the links ^.^

---

### Post by Alex_Moonshine on 2016-03-22
Well, the roguelikes (ADOM, DC, Nethack, etc.) are actually free, or in some cases, there is a free version, at least. But not everyone is into the adventures of the almighty @, I get it :)

---

### Post by mörgæs on 2016-03-22
> **BadassRare said:**
> I have like 2 laptops with a broke screen and one hp that is literally falling apart

Are any of these usable if you attach an external monitor to them? Stronger than the Intel 845 graphics?

---

### Post by BadassRare on 2016-03-22
Well i tried Nethack, not going to lie...i got so lost with its complexness but it looks so simple minded x_x thanks for the suggestions tho

---

### Post by BadassRare on 2016-03-22
> **mörgæs said:**
> Are any of these usable if you attach an external monitor to them? Stronger than the Intel 845 graphics?

the two best ones i have do not have a external monitor slot like my hp does. The hp which is the one falling apart works however it bluescreens very badly or if you push up at the bottem it fritzs out and looks like something out of a acid trip untill you unplug it

EDIT: the hp 2000 which half works is like i said falling out from the bottem and something is loose. I have tried to get it to work but i keep getting the same issues plus the usb drives don't work on it either so its hard if it is adriver which is what a neighbor told me i can't install linux onto it x_x

---

### Post by mastablasta on 2016-03-22
not sure how short you are on cash but 1st Gen Core i5 go for about 100-150 USD (depends on the build etc.).

anyway back to what it can run. like I said various software accelerated games from DOS era should work just fine. plenty are now considered to be abandonware (no one selling them, no one maintaineing them, no one prosecuting for download and copying them) and can be found over the internet. DBGL is a nice Linux GUI launcher for these old DOS games. use light desktop environment to conserve your resources.

there are also interesting text based MMO games if you are into text adventures. you connect to them from terminal. :)

there are a few lighter games in playdeb or on software center. like OpenTTD. plenty quake engine (1,2,3) based multiplayer games have bots available and are free (World of Padman, Enemy Territory, UFO AI...). 

you can check websites like reloaded.org that offer freeware, remakes & opensource games. though aimed at windows some games of those work on lower specs, have Linux version or might work nicely in wine.

regarding nethack I do hope you tried the graphics version. still notoriously difficult game that requires player to adapt a lot to survive. and even then you can easily get killed. 

a stonger GPU card and more RAM would help if this is a desktop. some old used GPU are sold at very low prices or maybe can be found being given away for free.

---

### Post by mr-daniel-lemke on 2016-03-22
AssaultCube is a free FPS that should run well on those specs. It is kind of like a CounterStrike/Quake mix and you can usually find at least a couple matches. Warzone 2100 and FreeCiv are both good strategy games. There's plenty of arcade/puzzle games on the Software Center that you should be able to run.

---

### Post by BadassRare on 2016-05-07
Thank you all so much for suggestions. Apologys for the very late response but i have played assultcube before and it lags on my system to the point of being unplayable. Which is honestly supriseing. I think its more where i am useing Ubuntu instead of lubuntu or even xubuntu or arch because i remember haveing 9.04 and assault cube never lagged. however where im useing 12.04 it lags enough that even on lowest settings i lag around on it. as for the dos games i found a few to tinker with which i already been through a few times and have been looking/working on new projects. which i may post questions about considering i have ran into quite a few problems on each.

---

