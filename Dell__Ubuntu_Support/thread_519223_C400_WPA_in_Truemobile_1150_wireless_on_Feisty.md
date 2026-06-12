---
title: "C400 WPA in Truemobile 1150 wireless on Feisty"
date: 2007-08-06
forum: Dell  Ubuntu Support
---

### Post by EdTheUniqueGeek on 2007-08-06
Has anyone been able to get WPA in the Dell Truemobile 1150 mini-PCI to work in 7.04 yet?
I've installed Wicd Manager and see my AP and even have a drop-down selection for WPA 1/2. But, when I type in the password key it accepts but I can never connect. I never get an error message just a cycle stage of it trying to authenticate and then it gets to the point of trying to obtain an IP but never gets an IP. I even assign a static IP but never get network access.
I've even gone as far as using ndiswrapper to use the Dell drivers I know work in Windows XP to allow WPA, but this does not seem to work either.
I see in the Wicd Manager under preferences to select a WPA Supplicant Driver. Is there a correct selection here that I should be using from the drop-down? I've tried a few but can never get network access.
Any help would be greatly appreciated.

---

### Post by moore.bryan on 2007-08-06
> **EdTheUniqueGeek said:**
> I've installed Wicd Manager and see my AP and even have a drop-down selection for WPA 1/2. But, when I type in the password key it accepts but I can never connect. I never get an error message just a cycle stage of it trying to authenticate and then it gets to the point of trying to obtain an IP but never gets an IP. I even assign a static IP but never get network access.
I've even gone as far as using ndiswrapper to use the Dell drivers I know work in Windows XP to allow WPA, but this does not seem to work either.
I see in the Wicd Manager under preferences to select a WPA Supplicant Driver. Is there a correct selection here that I should be using from the drop-down? I've tried a few but can never get network access.
Any help would be greatly appreciated.
*in wicd's preferences, choose the best driver for the wpa supplicant choice... does your dell have broadcom (like so many)?  if so, choose that.  if you're using ndiswrapper, choose that one.  i don't have the same comp, but fooling around with wicd won't permanently break anything.  ;-)*

---

### Post by EdTheUniqueGeek on 2007-08-06
Well, as I understand it, the Truemobile 1150 has a Orinoco chipset in it. At least what I see when doing a **lshw** it list it as Orinoco.
See the output below:

ed@edubuntulaptop:~$ lshw
WARNING: you should run this program as super-user.
edubuntulaptop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Mobile Intel(R) Pentium(R) III CPU - M  1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.4
          size: 997MHz
          capacity: 997MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:e0000000-e7ffffff iomemory:f4f80000-f4ffffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=11
             resources: iomemory:d8000000-dfffffff iomemory:f4f00000-f4f7ffff
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:09:9b:ec
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=192.168.15.253 latency=32 maxlatency=10 mingnt=10 multicast=yes
                resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:f6000000-f6000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
                resources: iomemory:f6001000-f6001fff irq:5
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:3a000000-3a0003ff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:bd:1e:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b[QUOTE]ed@edubuntulaptop:~$ lshw
WARNING: you should run this program as super-user.
edubuntulaptop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Mobile Intel(R) Pentium(R) III CPU - M  1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.4
          size: 997MHz
          capacity: 997MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:e0000000-e7ffffff iomemory:f4f80000-f4ffffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=11
             resources: iomemory:d8000000-dfffffff iomemory:f4f00000-f4f7ffff
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:09:9b:ec
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=192.168.15.253 latency=32 maxlatency=10 mingnt=10 multicast=yes
                resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:f6000000-f6000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
                resources: iomemory:f6001000-f6001fff irq:5
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:3a000000-3a0003ff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:bd:1e:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b
ed@edubuntulaptop:~$ lshw
WARNING: you should run this program as super-user.
edubuntulaptop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 510MB
     *-cpu
          product: Mobile Intel(R) Pentium(R) III CPU - M  1000MHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.11.4
          size: 997MHz
          capacity: 997MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci
          description: Host bridge
          product: 82830 830 Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 04
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:e0000000-e7ffffff iomemory:f4f80000-f4ffffff irq:11
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82830 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0 maxlatency=11
             resources: iomemory:d8000000-dfffffff iomemory:f4f00000-f4f7ffff
        *-usb
             description: USB Controller
             product: 82801CA/CAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:bf80-bf9f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@02:00.0
                logical name: eth0
                version: 78
                serial: 00:0b:db:09:9b:ec
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=3c59x ip=192.168.15.253 latency=32 maxlatency=10 mingnt=10 multicast=yes
                resources: ioport:ec80-ecff iomemory:fafffc00-fafffc7f irq:11
           *-pcmcia:0
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:f6000000-f6000fff irq:11
           *-pcmcia:1
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 3
                bus info: pci@02:03.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=64
                resources: iomemory:f6001000-f6001fff irq:5
        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801CAM IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master scsi-host
             configuration: driver=ata_piix latency=0
             resources: ioport:1f0-1f7 ioport:3f4-3f3 ioport:170-177 ioport:374-373 ioport:bfa0-bfaf iomemory:3a000000-3a0003ff irq:11
        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=Intel ICH latency=0
             resources: ioport:d800-d8ff ioport:dc80-dcbf irq:5
        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:d400-d4ff ioport:dc00-dc7f irq:5
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:bd:1e:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10 multicast=yes wireless=IEEE 802.11b

---

### Post by moore.bryan on 2007-08-06
*what's the output of ```
sudo lspci
```?*

---

### Post by EdTheUniqueGeek on 2007-08-06
Hmmmm...looking at this I don't see my wireless card.

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)

---

### Post by moore.bryan on 2007-08-06
*eureka!  it doesn't seem as though your wireless card is loaded at startup... is this a post-purchase card or did it come bundled in the comp?*

---

### Post by EdTheUniqueGeek on 2007-08-06
It's a post-purchase from Dell that I installed myself.
The card works though. I had it running in Windows XP using the most current drivers from Dell that had WPA implementation.

---

### Post by EdTheUniqueGeek on 2007-08-07
> eureka! it doesn't seem as though your wireless card is loaded at startup... is this a post-purchase card or did it come bundled in the comp?


Also, I just remembered.
If the wireless card is not being loaded at startup, how is it possible I can connect to an open AP in my neighborhood?

---

### Post by EdTheUniqueGeek on 2007-08-08
Does anyone have any thoughts on this? Any ideas on getting WPA to work with my scenario?
Thanks in advance.

---

### Post by moore.bryan on 2007-08-08
*hmm... let me think on this one and get back to you.*

---

### Post by moore.bryan on 2007-08-09
*could you post the exact name/details for the card you're using?*

---

### Post by EdTheUniqueGeek on 2007-08-09
All that I know is that it is a Dell Truemobile 1150.
Is there a command line in Ubuntu that will give me full details? If so, I will have to do that when I get home as my laptop is not with me today at work.
The *lshw* output I posted earliar states that it is a Orinoco driver.

**driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.10**

---

### Post by imdano on 2007-08-09
Can you connect to unencrypted networks?

---

### Post by moore.bryan on 2007-08-09
*after looking around a bit, it seems as though the original drivers/firmware for the truemobile 1150 did not include wpa support.  have you installed all the latest drivers/firmware?  i found [this]("http://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R143355&formatcnt=1&libid=0&fileid=191429") on the dell site...*

---

### Post by EdTheUniqueGeek on 2007-08-09
> Can you connect to unencrypted networks?

I can connect to unencrypted and WEP encrypted access points.

> after looking around a bit, it seems as though the original drivers/firmware for the truemobile 1150 did not include wpa support. have you installed all the latest drivers/firmware? i found this on the dell site...

I had previously tried using ndiswrapper and selecting the latest Dell drives that was supposed to make the card WPA capable, but I was still not able to see a WPA option in the drop-down, just WEP.
I question if the ndiswrapper is actually doing the job. I installed it from Synaptic Manager with the GUI interface. I use this GUI to access the drivers.

---

### Post by moore.bryan on 2007-08-09
*i'd go back and check to make sure wicd is using ndiswrapper then and specifying the wap passphrase there...*

---

### Post by EdTheUniqueGeek on 2007-08-09
Oh. By the way, that link to the Dell drivers is for the Truemobile 1300 and 1400 cards.
This is the driver that I use for my specific card to give it WPA.

[Dell link to driver page]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R69905&SystemID=LAT_PNT_P3_C400&servicetag=&os=WW1&osl=en&deviceid=2491&devlib=0&typecnt=0&vercnt=2&catid=5&impid=-1&formatcnt=1&libid=5&fileid=90951")

---

### Post by imdano on 2007-08-09
The ndiswrapper in the repos is an older version and notoriously bad with wireless drivers.  You should compile the newest version from source.  If you search the forums a little there a bunch of guides for it.

---

### Post by EdTheUniqueGeek on 2007-08-09
Okay. I will try that.
Thanks.

---

### Post by EdTheUniqueGeek on 2007-08-10
Here's an update:

Okay. I was mistaken about being able to connect to an encrypted AP. I thought through all my troubleshooting in attempting to connect to multiple APs that at one time I was able to. I went home last night an changed my wireless router (Apple Airport Extreme) from WPA to WEP (passphrase) and I was not able to connect. Oddly enough, I can enter in the settings in Ubuntu by selecting the drop-down for WEP with passphrase but it would never connect.
Just for the hell of it, I tried changing my router to something other than WEP and WPA by trying WPA2 Personal with AES. I was able to select a hidden network in Ubuntu, type in the SSID, see and select in the drop-down WPA2 Personal with AES. Once selected, I got further than I ever had before. Before, I would get to 28%, never connect, and it would recycle the process. This time with WPA2 Personal it got past 28% to 57% but would never connect.
I think this is all very odd. I'm really confused at how Ubuntu is handling my wireless card. It sees the card correctly in the network manager GUI as Dell Truemobile 1150, the security is visible in the drop-down but it can never connect to the AP with security enabled. Only if the AP is open can I connect to it.
Can someone explain why this is?
Also, other than this wonderful forum (seriously, the response is great in this forum. I have found the Ubuntu community to be awesome), does Ubuntu offer technical support for stuff like this?

---

### Post by imdano on 2007-08-10
Well, I took a look at the orinoco driver source code and there doesn't appear to be any wpa support in there.  It's able to see the card correctly and get scan results because the card and driver are working properly, it's just that the driver doesn't support connecting to WPA networks.  It's probably able to display the WPA networks properly because it's just parsing results it gets from the firmware (I'm guessing here, I don't know much about how drivers work).  You *should* be able to connect to a WEP network though, the driver had quite a bit of code for handling WEP.

I'd try compiling the newest version of ndiswrapper from source and giving windows drivers a shot.

---

### Post by EdTheUniqueGeek on 2007-08-10
Are you looking at the Orinoco driver source code from the default install of Feisty?
The reason I ask is because the Dell has a driver for this card that gives the card WPA support, I've used it successfully in Windows XP.
I think I am just having a hard time loading that Dell driver in ndiswrapper.

---

### Post by imdano on 2007-08-10
> **EdTheUniqueGeek said:**
> Are you looking at the Orinoco driver source code from the default install of Feisty?Yes.

I don't really know a whole lot about ndiswrapper so I probably won't be too much help there.  Where are you in the install/configuration process?

---

### Post by EdTheUniqueGeek on 2007-08-10
Well, I put a fresh install of Feisty back on this morning before going to work. I plan to spend some more time on the ndiswrapper portion tonight when I get home from work.

---

### Post by EdTheUniqueGeek on 2007-08-13
Well, this is getting a bit annoying.
I rebuilt and installed ndiswrapper to the best of my ability. However, I'm not sure if it installed correctly.
Either way, when I do a **ndiswrapper -l**, after installing the Dell Windows XP driver to give the card WPA capability, I get the following:

*wldel48b : invalid driver!*

Which is the name of the .inf file from the Dell drivers.
That can't be good. I'm not too familiar with ndiswrapper but I would think that no matter what, it would load whatever Windows driver you install.
Any ndiswrapper experts around that could help with this?

---

### Post by EdTheUniqueGeek on 2007-08-13
I tried reinstalling ndiswrapper again and this is what I get (I think I saw this before):

**ed@c400ubuntu:~/ndiswrapper-1.47$ sudo make uninstall**
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
**ed@c400ubuntu:~/ndiswrapper-1.47$ sudo make uninstall**
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
**ed@c400ubuntu:~/ndiswrapper-1.47$ sudo make**
make -C driver
make[1]: Entering directory `/home/ed/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/ed/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/ed/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/ed/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/ed/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ed/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/ed/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/ed/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/ed/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/ed/ndiswrapper-1.47/utils'
make: *** [all] Error 2
**ed@c400ubuntu:~/ndiswrapper-1.47$ sudo make install**
^[[5~make -C driver install
make[1]: Entering directory `/home/ed/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/ed/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
echo /lib/modules/2.6.20-16-generic/misc
/lib/modules/2.6.20-16-generic/misc
mkdir -p /lib/modules/2.6.20-16-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-16-generic/misc
/sbin/depmod -a 2.6.20-16-generic -b /
make[1]: Leaving directory `/home/ed/ndiswrapper-1.47/driver'
make -C utils install
make[1]: Entering directory `/home/ed/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/ed/ndiswrapper-1.47/utils'
make: *** [install] Error 2

---

### Post by imdano on 2007-08-13
That didn't get installed correctly.  Make sure you've completely uninstalled ndiswrapper, then open up a terminal and type ```
sudo apt-get install build-essential
```Then try compiling ndiswrapper again.

---

### Post by EdTheUniqueGeek on 2007-08-13
I've uninstalled and reinstalled using Synaptic Package Manager this time. However, I still don't think it is installing correctly.

Check this out:

**ed@c400ubuntu:/$ ndiswrapper -v**
utils Error: no version specified!
driver modinfo: could not open /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko: No such file or directory

I've seen this exact error before when manually installing from command line.
Is there a problem with the latest kernel, possibly?

---

### Post by imdano on 2007-08-13
Did you still get a bunch of errors when you installed?  Did you install build-essential?  The logs you posted indicated that make couldn't find stuff like stlib.h, which I'm pretty sure shouldn't happen if build-essential is installed.

---

### Post by EdTheUniqueGeek on 2007-08-13
Okay. Finally got ndiswrapper installed correctly.

**ed@c400ubuntu:~/ndiswrapper-1.47$ ndiswrapper -v**
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

However, it still list as an invalid driver:

**ed@c400ubuntu:~/ndiswrapper-1.47$ ndiswrapper -l**
wldel48b : invalid driver!

I tried uninstalling the driver to reinstall but it can't find it to uninstall:

**ed@c400ubuntu:~/ndiswrapper-1.47$ sudo ndiswrapper -r WLDEL48B.INF**
couldn't delete /etc/ndiswrapper/WLDEL48B.INF: No such file or directory

If it is stating no such file or directory, then I could see why it would be listed as an invalid driver. Right?

---

### Post by EdTheUniqueGeek on 2007-08-13
I was able to remove and re-install the driver however it still list as an invalid driver.
I guess this driver is unusable?

---

### Post by imdano on 2007-08-13
I have a feeling that you just need to do a couple of ndiswrapper commands or a modprobe to fix your problem, but unfortunately I don't know much about ndiswrapper configuration.  I'm sure someone with some ndiswrapper experience will be able to help you.

---

### Post by EdTheUniqueGeek on 2007-08-13
Thank you.
I might just post a new thread under the Network & Wireless section to see if anyone has any ideas why the driver displays invalid.

---

### Post by kgr132 on 2007-08-13
I don't know for sure about the Dell 1150. I think I have a Dell 1350 in my D600. When I run **lspci** it reports that I have a Broadcom 4306. Anyway, I found the Dell drivers to be crap and got the same kind of error you did when I tried to use them with ndiswrapper. After a LOT of searching in these forums for the Broadcom 43xx series cards. I came across some drivers that worked much better for me here:
[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) (for everything that's BCM43xx EXCEPT the Broadcom 4318 )
or
[http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip](http://dlsvr03.asus.com/pub/ASUS/wireless/WL-100g-03/Driverv3100640.zip) (for the 4318 )
Maybe one of these will work better for you.

I've lost the bookmark to original post where I got this info. All I've got left is few notes I made. Sorry.
BTW, for the .exe file liked above, you'll need a tool called cabextract that will let you take the file apart and get at the driver files:
sudo apt-get install cabextract
cabextract sp33008.exe

Either way, I got the ndiswrapper driver to work but I still have trouble getting WPA to work. There's a known bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103768](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103768)
regarding the Broadcom drivers and the 2.6.20 kernel that may be at the root of the problem.

There's a patch by Tim Gardner listed in the bug report that may help. I haven't been able to try it yet myself. I'm away from home and can't test my encrypted connections right now, but WPA still wasn't working for me as of last week.

We may have to wait for the Gutsy release in October to get some resolution on this, but I hope not.

Hope this helps a little. Good Luck.
-K-

---

### Post by EdTheUniqueGeek on 2007-08-13
Thank you so much for that information.
Unfortunately, I believe the core of my 1150 is Orinoco not Broadcom. Which stinks either way. I've heard that a lot of people are having issues with the Broadcom chipsets too. We use the D610 at work which, actually, comes either with a Broadcom or Intel chipset. My manager has the Broadcom and he has been trying for ages to get WPA working have loading the drivers via ndiswrapper with no luck.
There is a good chance that we will have to wait for the next kernel update or Gutsy before these issues are resolved. Until then, I have dual install of Windows XP and Ubuntu. Windows for the WPA and Ubuntu for everything else.
I was really hoping to avoid Windows completely on this laptop. But, I will press on. I've also posted a thread in the Networking category.

[http://ubuntuforums.org/showthread.php?t=524829]("http://ubuntuforums.org/showthread.php?t=524829")

Thanks again.

---

### Post by moore.bryan on 2007-08-14
*just to double-check, try typing ```
sudo iwlist eth1 key
``` where "eth1" is your wireless card...*

---

