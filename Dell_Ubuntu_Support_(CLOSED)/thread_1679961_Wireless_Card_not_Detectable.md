---
title: "Wireless Card not Detectable"
date: 2011-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by srlang on 2011-02-01
Hi,

I just yesterday decided to dual boot Ubuntu on my Vista Dell Inspiron. After the first time I turned off the laptop, Ubuntu would not allow me to connect to my home network. I have switched in between the two OS's to make sure that the wireless receiver is turned on, but Ubuntu does not recognize it as being enabled. Manually plugging in a wire is recognized, but the wireless card is not. 

When I type the correct information in the terminal (lshw -C network) or whatever it is, I keep being told that wireless is DISABLED. Looking through the Ubuntu Help documentation, it tells me to make sure the switch is on, which through Vista, I have.

Any help with getting Linux to recognize the wireless card is helpful. (Sorry, no model numbers yet, I'm working on getting those.)

Thanks.

---

### Post by mikewhatever on 2011-02-02
You should post the output of lshw -C ... to let us look as well.

---

### Post by srlang on 2011-02-03
Sorry, posted this from the vista portion because I had homework and couldn't afford the time.

username@ubuntu:~$ lshw -C
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

username@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:2e:b3:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:24:87:77
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=10.0.1.17 latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)

---

### Post by ugm6hr on 2011-02-05
> **srlang said:**
> 
  *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:2e:b3:64
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:f69fe000-f69fffff
 

Looks like you are using the correct driver (iwlagn), but there is a problem with it being turned off.

Have a look at this thread for advice on how to check:
[http://art.ubuntuforums.org/showthread.php?t=1672582](http://art.ubuntuforums.org/showthread.php?t=1672582)

---

### Post by srlang on 2011-02-06
Thanks for the link, it worked beautifully.

I'll actually start reading the pages on how to self-diagnose these issues so I can stop being the reliant one.

Thanks again.

---

