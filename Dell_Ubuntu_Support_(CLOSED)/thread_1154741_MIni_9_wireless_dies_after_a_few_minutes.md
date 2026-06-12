---
title: "MIni 9 wireless dies after a few minutes"
date: 2009-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anjilslaire on 2009-05-10
I've been running the Jaunty Netbook Remix since it went final a few weeks back. I've recently noticed that after connecting to my AP for a couple of minutes, I lose ping and all network connectivity, even though it still shows as connected to teh router, with an IP.

Router set to SSID hidden, WPA2 AES. This setup worked flawlessly in 8.10.
Proprietary STA driver is enabled.
Ping now results in
```

ping: sendmsg: No buffer space available

```

Kernel: 2.6.28-11

Relevant lspci
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

lshw
```

*-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth1
                version: 01
                serial: 00:21:63:ae:5b:05
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```

Has anyone seen this? The mini still reports being connected to the AP, bit I can't pin or get anywhere, either on the internet or inside my lan.

Thoughts?

UPDATE: Solved
I tried an experiment, setting the mini on a very cool surface (stone tile flooring) overnight, pinging the gateway. After ~7 hours, I checked it this morning: Zero packet loss, under side was nice and cool, right where the wireless card is located.
My deduction is that this thing overheats easily in warm weather on my lap, which is causing significant blockage to the passive vents on the bottom, right where the wifi card sits.

So, if anyone else starts getting erratic behavior, try keeping it on a flat cool surface.

I feel stupid for not trying this earlier.

---

### Post by anjilslaire on 2009-05-19
Alright,
I'm really beginning to wonder what's up. It's begun to drop again, after about 10 minutes. 
Again, network manager reports that connectivity is solid, and eth1 reports a valid IP from the router, but I get no access or ping after about 10 minutes, reliably. A reboot usually fixes it about 75% of the time, giving me another 10 minutes or so.

Definitely a big hamper on my Mini's intended use.

Has anyone else experienced this? Could the wireless card be going bad?

---

### Post by ugm6hr on 2009-05-19
I'm on WPA-TKIP, but have had no problems at all on 9.04NBR and Mini 9.

I have tried UPnP media serving to it from my FreeNAS, and managed 2 hours without a problem.  Only been on 9.04 for a few days though, so I'll keep you informed if anything new happens.

---

### Post by anjilslaire on 2009-05-19
Looks like there's a bug already for it:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192765)

Unfortunately Jaunty backports did nothing to help :(

---

### Post by anjilslaire on 2009-06-03
Strangely enough, the wifi has started behaving itself perfectly again, with no apparent kernel or networking updates that I've noticed. We'll see how long it lasts (2 full battery charges so far, about 6+ hours worth of surfing, etc)

In any event, I orderd an intel card a couple of days ago, so I'll have a backup in case it goes bely up again.

---

