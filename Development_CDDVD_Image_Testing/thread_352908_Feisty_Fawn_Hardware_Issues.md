---
title: "Feisty Fawn Hardware Issues"
date: 2007-02-03
forum: Development CD/DVD Image Testing
---

### Post by ScottMorris on 2007-02-03
Hey there,  I just booted up Herd 3 of 7.04 and I found some Hardware problems.

First:  It detects my Onboard Ethernet card just fine but it doesn't load any drivers for my wireless adapter.  But it worked in herd 2 so I wonder what changed.  Below is the lshw info..

```
*-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@02:01.0
                logical name: eth0
                version: 10
                serial: 00:02:3f:d2:92:61
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28
 latency=32 maxlatency=64 mingnt=32 multicast=yes
                resources: ioport:3000-30ff iomemory:c2014800-c20148ff irq:21
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 2
                bus info: pci@02:02.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=168 maxlatency=28 mingnt=10
                resources: iomemory:c2000000-c200ffff irq:23
```


As well it is incorrecly detecting the size of my video card.  Its an nVidia GeForce 4 5600 Go with 64 MB dedicated GRAM but it is seeing it at 256 MB...

  ```
*-display
                description: VGA compatible controller
                product: NV31M [GeForce FX Go5600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a1
                size: 256MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: latency=40 maxlatency=1 mingnt=5
                resources: iomemory:c1000000-c1ffffff iomemory:e0000000-efffffff
 irq:10
```

Also it isn't setting my AC '97 sound device, but herd 2 did...
```
*-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: ioport:1c00-1cff ioport:18c0-18ff iomemory:c0000c00-c000
0dff iomemory:c0000800-c00008ff irq:10
```

Or my internal SD Card reader...
```
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: 6
                bus info: pci@02:06.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:c2014c00-c2014dff irq:10
```

Or my PC Card controller which has my Creative sound card in it..
```
           *-pcmcia UNCLAIMED
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: 4
                bus info: pci@02:04.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: latency=0 maxlatency=3
                resources: iomemory:c2015000-c2015fff irq:16
```


I'm not sure where to put this information but as well when booting it stops and I have to hit Ctrl + Alt + Del to get it to stop what its doing then it loads X and I can use GNOME and test out some stuff.

I wonder why this is broken in Herd 3, are they phasing out the mad wifi drivers or the AC '97 ones?  Or is this just one of the stadard bugs that are run into during development.

---

### Post by pochu on 2007-02-04
Hi ScottMorris!

Please, report this problems in [Launchpad]("https://bugs.launchpad.net/ubuntu/+filebug"), if they haven't been reported yet, in order to fix them in Ubuntu.

Thanks
Pochu

---

### Post by pmshirey on 2007-02-04
Dood, I think you are trying to configure wireless. (Just guessing since you didn't mention that in your post.) Well here is the first thing you need to do. Install ndiswrapper. Here are the steps.[LIST=1]
[*]Instert a Live CD
[*]Go to synaptic package manager
[*]click on search
[*]type,"ndiswrapper"(without quotes) in the search box
[*]click search
[*]right click on the package ndiswrapper-custom and click mark for installation
[*]right click on the package ndiswrapper-utils 1.8 
[*]click apply
[/LIST]
Now you have ndiswrapper installed:)

---

### Post by ScottMorris on 2007-02-05
My wireless card has always worked in the stable versions of Ubuntu and it worked fine with Herd 2 of Fawn, but now with Herd 3 it doesn't, that was what made me look at what other hardware wasn't configured.

---

### Post by Alessandro.p on 2007-02-06
I also have some hardware issue, i think the kernel has some problem...
I upgraded from edgy to feisty herd 3, so i dont know if in the herd 2 the kernel was ok...
I can only boot if a give to grub this option: acpi=off

Post a dmesg, after a bootup, so we can see if there is some common message between you and me... I think there are some IRQ problems

---

