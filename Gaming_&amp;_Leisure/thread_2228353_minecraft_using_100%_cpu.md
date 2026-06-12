---
title: "minecraft using 100% cpu"
date: 2014-06-06
forum: Gaming &amp; Leisure
---

### Post by aramil248 on 2014-06-06
when i run minecraft its using using 100% of my cpu with 5fps in singleplayer but its only using 30% ram is there anyway to stop minecraft from using all of my cpu and lag alot less?

---

### Post by nsync on 2014-06-07
What are ur sys. specs?

---

### Post by dannyboy79 on 2014-06-07
not sure if it will help, but can't you use the minecraft launcher and specify you want it to use more RAM? maybe using more RAM it will use less CPU.

---

### Post by Buddhalobes on 2014-06-08
Hi, I'm having a similar issue so I decided to make my account and post my system specs. 

MacBookPro 7,1 running Ubuntu 14.04 AMD x64 +Mac
Prossesor: Intel® Core&#8482;2 Duo CPU P8600 @ 2.40GHz × 2
Graphics: GeForce 320M/integrated/SSE2
Memory: 3.6 GiB (I have 4 gigs but I guess ubuntu takes into account what it needs to run and displays the rest)
Using OpenJDK Java7 Runtime

I'm using the ATLauncher to play both modded and vanilla Minecraft and have allocated 2.5 GiB to the launcher through it's built in settings. I launched the CrackPack (150 or so mods in the pack). Within an hour of launching I heard audio studdering and noticed slightly more fps choppyness than is normal moments before my screen froze and locked me from moving my mouse and acssesing terminal or any other keyboard shortcuts I could think of. I powered off with the powerbutton and retried with reckless abandon for the next few hours with more of the same result only it happend sooner with each attempt with the last one being moments after launch. This was yesterday (8/6/14).

Today I attempted to play vanila minecraft through the launcher and I had Htop open as a just in case alt-tab if problems arose, which they did. about 10 minutes in I noticed fps studdering but I chalked it up to it being the first night in minecraft chilling in a village with zombies moaning about. By the next night I had gotten rid of most of the zombies ability to span in the village but I was still getting choppy fps and a bit of input lag so I alt-tabed to htop and organized by cpu to see that both cpu cores were alternating between 70% and 100% (with 1 always at 100%) and all 2.5 GiB of allocated ram was being used across 2 java prosseses. This never happened in windows for me and I would dump my free time into modded minecraft, I need to craft. Hope this will help.

Thanks.

---

### Post by mastablasta on 2014-06-09
i take it that all desktop effects are off when you play it?

i have E3300 celeron (dualcore)  with 1,3GB ram and it seems to run fine so far (Kubuntu). this computer acts as client while the server one is single core with 32 bit windowsXP home and 4GB ram. seems to be working fine. ok occasinally it lags (lots of TNT, train...), but otherwise it goes fine.

i am not sure why it is showing 3.6GB ram for you. i am not sure that is usual. but depends where you are wathicn ght ram i guess. the free -m command should show it well

---

### Post by Buddhalobes on 2014-06-09
> i take it that all desktop effects are off when you play it?
Not sure how to so probably no.

free -m is showing me 3690 under total but I personnaly put 4 gigs in this since it shipped with just 1 gig.

---

### Post by aramil248 on 2014-06-09
is this the specs you wanted? ```
computer    description: Desktop Computer
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: i845
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG
          date: 05/25/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 1.70GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.1.3
          slot: Socket 478
          size: 1700MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pebs bts
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 20KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1536MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             physical id: 0
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             physical id: 1
             slot: A1
             size: 512MiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             physical id: 2
             slot: A2
             size: 512MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: memory:ec000000-edffffff memory:e0000000-e7ffffff
           *-display
                description: VGA compatible controller
                product: NV34 [GeForce FX 5200]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: irq:10 memory:ec000000-ecffffff memory:e0000000-e7ffffff memory:ed000000-ed01ffff
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:ee000000-ee0fffff
           *-network
                description: Ethernet interface
                product: RTL8139 Ethernet
                vendor: D-Link System Inc
                physical id: b
                bus info: pci@0000:02:0b.0
                logical name: eth0
                version: 10
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=[REMOVED] latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
                resources: irq:11 ioport:c000(size=256) memory:ee000000-ee0000ff
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-usb:0
             description: USB controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:d000(size=32)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:5000(size=16)
        *-usb:1
             description: USB controller
             product: 82801BA/BAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:5 ioport:d800(size=32)
        *-communication UNCLAIMED
             description: Modem
             product: 82801BA/BAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:e400(size=256) ioport:e800(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk:0
             description: ATA Disk
             product: Maxtor 6Y060L0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: YAR4
             serial: [REMOVED]
             size: 57GiB (61GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=0009b9c6
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 57GiB
                capacity: 57GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-06-04 13:45:29 filesystem=ext4 lastmountpoint=/ modified=2014-06-09 18:31:16 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2014-06-09 18:31:17 state=mounted
        *-disk:1
             description: ATA Disk
             product: Maxtor 6E030L0
             vendor: Maxtor
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/sdb
             version: NAR6
             serial: [REMOVED]
             size: 28GiB (30GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=9c5cdae6-06b4-4084-9fb9-a1c1a7cc68d5 sectorsize=512
           *-volume
                description: System partition
                vendor: EFI
                physical id: 1
                bus info: scsi@0:0.1.0,1
                logical name: /dev/sdb1
                serial: [REMOVED]
                capacity: 28GiB
                capabilities: boot
                configuration: name=primary
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: SCSI CD-ROM
             product: Drive/G6D
             vendor: CD-ROM
             physical id: 0.1.0
             bus info: scsi@1:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.30
             capabilities: removable audio
             configuration: ansiversion=5 status=nodisc



```

---

### Post by dannyboy79 on 2014-06-09
yeah, unfortunately you're trying to run minecraft on a very underpowered machine. a celeron 1.7Ghz with only 1.5GB of ram and built in graphics may struggle to even play minecraft sadly.

---

### Post by aramil248 on 2014-06-09
it runs everything else but minecraft good i think it must be java because even runescape lags for me

---

### Post by Buddhalobes on 2014-06-10
> it runs everything else but minecraft good i think it must be java because even runescape lags for me

What else do you play on that machine because I cant think of much that could run ok on.
> 
[QUOTE]i take it that all desktop effects are off when you play it?

Not sure how to so probably no.[/QUOTE]

I'm still not sure how to disable desktop effects fully just while I'm playing (I like how unity looks too much to give it up full time) but I got Unity tweek tool and made some adjustments that also boosted my mincraft fps before it locked up on me again. I'm going to try using the nvidia legacy 304.117 proprietary rather than the Nvidia legacy 304.121 Open source driver next and I'll post my findings.

---

### Post by mastablasta on 2014-06-10
> **aramil248 said:**
> it runs everything else but minecraft good i think it must be java because even runescape lags for me

did you try with oracle java if it makes a difference? but yes, the CPU is kind of weak. and this game is CPu intensive i believe.

> **Buddhalobes said:**
> 
I'm still not sure how to disable desktop effects fully just while I'm playing (I like how unity looks too much to give it up full time) but I got Unity tweek tool and made some adjustments that also boosted my mincraft fps before it locked up on me again. I'm going to try using the nvidia legacy 304.117 proprietary rather than the Nvidia legacy 304.121 Open source driver next and I'll post my findings.

i am not sure how to do it in unity, but in KDE it's preety simple. you just untic a box and then when anyhting fullscreen is ran it turns off the desktop effects for that time.

if you find out that the Unity is the one taking resources a simple solution would be to add a very light Windows manager (e.g. icewm, jwm) and then when you want to game just logout and into icewm and start your game.

---

### Post by aramil248 on 2014-06-10
i play star wars jedi knight jedi academy, openarena and unreal tournament 2004 to name a few

---

### Post by mastablasta on 2014-06-11
> **aramil248 said:**
> i play star wars jedi knight jedi academy, openarena and unreal tournament 2004 to name a few

then it should handle it reasonably well. however all those games are better optimised. also minecraft is preety CPU intensive. while those other games might be using GPU more. still if you can play all those games on mid/high setting it should probably work better in minecraft. 

there is a command you could use to speed it up a bit. i don't know it right now so i would need to check at home if computer is not occupied.

have you tried the Oracle Java?

---

### Post by aramil248 on 2014-06-11
i dont rember what type of java i have installed i did it by apt-get

---

### Post by Buddhalobes on 2014-06-11
After switching graphics drivers to nvidia legacy 304.117 by way of `sudo apt-get nvidia-current-updates`, updating with Software Updater and cold booting, I am now unable to log into minecraft. 

I've redowloaded the launcher, reinstalled OpenJDK, checked my login to make sure it was correct and checked Mojang to see if they are up. No luck.

I'm at a loss now.

---

### Post by mastablasta on 2014-06-12
> **aramil248 said:**
> i dont rember what type of java i have installed i did it by apt-get

that one is opensource Java actually called IceTea or something like that.

---

### Post by Buddhalobes on 2014-06-12
> After switching graphics drivers to nvidia legacy 304.117 by way of  `sudo apt-get nvidia-current-updates`, updating with Software Updater  and cold booting, I am now unable to log into minecraft.

UFW was preventing me from logging in, I turned it on while fumbling around with my other Minecraft issues. Also now I think I can modify my personal settings. *This was All part of my master plan and not at all me fumbling around like an idiot*

---

### Post by wolflint on 2014-06-12
Have you changed the drivers? The open-source drivers aren't suitable for gaming in my opinion.

---

### Post by aramil248 on 2014-06-12
> **mastablasta said:**
> that one is opensource Java actually called IceTea or something like that.
i think i have the oracle java installed i see stuff about it under preferences

---

### Post by mastablasta on 2014-06-13
this is how i launch it

[COLOR=#000000][FONT=Arial]java -Xms512M -Xmx512M -jar  '/home/*user*/.minecraft/minecraft launcher/MinecraftLauncher.jar'[/FONT][/COLOR]

i forgot what it does but works miracles on my old maschines

---

### Post by Joey_Bui on 2014-06-13
Me too when i run Assassin's creed with full Op....:sad::sad:

---

### Post by DarkAmbient on 2014-06-13
You could try Optifine, it's a mod that extends the tweaking ability of Minecraft. Which allows you to decrease the req. of Minecraft, or vice versa.

[http://optifine.net/downloads.php](http://optifine.net/downloads.php)

I managed to play Minecraft on atleast 20 fps on my old laptop with Arch Linux + xfce4, which has a 1.66Ghz cpu and only 512 MB of DDR-RAM.

---

### Post by Buddhalobes on 2014-06-13
> **DarkAmbient said:**
> You could try Optifine, it's a mod that extends the tweaking ability of Minecraft. Which allows you to decrease the req. of Minecraft, or vice versa.

[http://optifine.net/downloads.php](http://optifine.net/downloads.php)

I managed to play Minecraft on atleast 20 fps on my old laptop with Arch Linux + xfce4, which has a 1.66Ghz cpu and only 512 MB of DDR-RAM.

Unfortunately, this is not an issue of fps that can be addressed by dropping all settings to minimum and turning off all animations in game. This is an issue of the game, when loaded in a world, becoming completely unresponsive and forcing me to power down manually in order to regain my ability use my system. The usual suspects I am aware of have been ruled out over the last week or so and a solution has not been found.

---

### Post by efflandt on 2014-06-16
FX 5200 graphics was rather slow in its prime time, which was on a company desktop I got in 2003 and a personal desktop I bought in 2004. I promptly upgraded the video of that 2004 desktop, but also had to upgrade the PSU because the HP 250 watt PSU was overrated and could not boot half of that (125-130 watts at wall outlet after upgrading to 330 watt Antec PSU).

For anyone with integrated Intel video only, good luck. For some reason the Intel driver in Linux is significantly slower than in Windows even i7 2.4 GHz CPU with 8 threads. But fortunately my laptop also has nvidia graphics (GTX 765M).

---

### Post by aramil248 on 2014-06-29
> **mastablasta said:**
> this is how i launch it

[COLOR=#000000][FONT=Arial]java -Xms512M -Xmx512M -jar  '/home/*user*/.minecraft/minecraft launcher/MinecraftLauncher.jar'[/FONT][/COLOR]

i forgot what it does but works miracles on my old maschines
i tried it did not help also if i play any version above 1.7.2 i get 1-3fps on the main menu but on 1.7.2 and below i get about 10-20fps

---

### Post by Buddhalobes on 2014-10-25
I'd like to update this just in case someone comes accross this and is wondering. I switched out my HDD from the apple provided Hitachi (250gb, 2.5 inch sata, 5400rpm) to a Western digital (320gb, 2.5 inch sata 3, 5400 rpm) and just installed Ubuntu 14.04 LTS pretty much as is with only fixes found here [https://help.ubuntu.com/community/MacBookPro7-1/Trusty](https://help.ubuntu.com/community/MacBookPro7-1/Trusty).

Now everything runs significantly better, from the default unity environment to steam games to heavily modded minecraft. My issues were entirely hardware and there was very little that could be done to solve it aside from replacing the HDD. I joke now that minecraft on Ubuntu is an indicator of your system's health; If you can't run minecraft, start looking for new hardware.

Apologies for bumping an older post, but I felt it was relevant.
Thanks.

---

