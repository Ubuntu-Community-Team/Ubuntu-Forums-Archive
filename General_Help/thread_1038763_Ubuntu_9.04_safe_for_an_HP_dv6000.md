---
title: "Ubuntu 9.04 safe for an HP dv6000?"
date: 2009-01-13
forum: General Help
---

### Post by vonbrune on 2009-01-13
I'm planning to beta test your new Linux distribution of 9.04 and so I was wandering if 9.04 would work with an nvidia 7100 graphics card (I believe) an Atheros internet card (previously failed and I had to set it up for it to work on 8.10.) The main reason I want 9.04 is because during start up the loading bar stalls (fixed it with noapic) and sound just failed when I was trying to set up my internal mic and then I did a stand by after that nothing about sound worked  (haven't fixed yet but did everything possible and it still won't work.) I'm ok with ubuntu terminal but still a bit of a noob. Anything about 9.04 that is incompatible with an HP dv6000, I read somewhere that my data will be saved so I was wondering if I have to reset the atheros driver?

---

### Post by cariboo on 2009-01-13
Jaunty Alpha3 is scheduled  to come out on the 15th, but unless your really know what you are doing, and you are able to fix a lot of problems, I would suggest you wait until the beta comes out.

Jim

---

### Post by solwic on 2009-01-13
> **cariboo907 said:**
> Jaunty Alpha3 is scheduled  to come out on the 15th, but unless your really know what you are doing, and you are able to fix a lot of problems, I would suggest you wait until the beta comes out.

Jim

+1.  Sometimes (especially with laptops) the final release isn't even stable.  Alpha and Beta releases are not for amateurs.  Then again, if we don't experiment and push ourselves, we'll never be anything but amateurs....  After all, if you break something on your main system, you kind of have to fix it.  Necessity is the mother of invention, yes, but I believe it's also the mother of learning.  :)  

Of course, if you've got a spare machine sitting around...well, spare machines were made for Alpha/Beta releases....  :)

---

### Post by vonbrune on 2009-01-13
Well thank you... but all I really need to know is if ubuntu 9.04 alpha 2 or 3 comes with support for atheros drivers.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:24:f8:26:8c
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1e:4c:95:71:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.64 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:92:83:f8:1f:cd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


EDIT:
Great support by the way... You guys respond really fast!

---

### Post by vonbrune on 2009-01-15
If I do wait until April 23, 2009 for the new Ubuntu, will I still be able to use my wireless? Or will it switch to the old card?

---

### Post by vonbrune on 2009-01-28
Setting up my wireless on ubuntu 8.10 was a difficulty but now that I know about linux back ports which does it in 2 seconds I think I'll use 9.04 beta 4 when it comes out. Or I will just wait until April 23.

---

### Post by tim183 on 2009-02-09
I had the same computer, I tried for months to get the wirless working with an Atheros ar5007eg card.

In the end I went and bought a Broadcom wireless carthrough an HP parts dealer for about US$20. That worked perfectly out of the box after activating the driver (module).

I read that the Broadcom drivers were getting alot of attention as they were the cards being used in those swank loonking new Dell desktops.

---

