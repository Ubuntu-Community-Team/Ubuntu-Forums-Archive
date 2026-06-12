---
title: "Wake On Lan - Dell 5150c - Is it possible?"
date: 2008-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by firefly2005 on 2008-12-22
Hi everyone.. Firstly my apologies if this is posted in the wrong place

For the last couple of hours i have been trying to get my dell 5150c to Wake on LAN with no luck! :confused:

I have looked through the BIOS settings and there is nothing to suggest that it is Wolable! The closest thing to Wol i could find is PXE :(

I'm using an Ethernet connection on Intrepid (eth0) and the NIC is inbuilt.

Ethtool reports:

```
Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x00000007 (7)
        Link detected: yes
```

Am i right in thinking that it is possible to Wake on LAN? And if so is there a special way of enabling it? I have (or at least i think) enabled wol in intrepid .. Any Ideas?

Thank You in advance!! :P

Firefly2005

---

