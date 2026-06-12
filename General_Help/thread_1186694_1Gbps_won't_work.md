---
title: "1Gbps won't work"
date: 2009-06-13
forum: General Help
---

### Post by orrie on 2009-06-13
We have to computers here in the network where we've tried to transfer files with 1Gb/s, but this won't work.

The cable is Cat5e and both networkcards is supporting 1Gb/s.

The output from ethtool on PC #1 is:
```

Settings for eth0:
Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Half 1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: pg
Wake-on: d
Current message level: 0x000000ff (255)
Link detected: yes

```

The output from ethtool on PC #2 is:
```

Settings for eth0:
Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: MII
PHYAD: 1
Transceiver: external
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Link detected: yes

```


I've made the Cat5e-cable myself.
With the "correct" order.
1: White-orange
2: Orange
3: White-green
4: Blue
5: White-blue
6: Green
7: White-brown
8: Brown


We have tried to connect the cat5e cable directly between both computers without any success.
And through an Gigabit Ethernet router without any success also.
The transfer rate through sftp is at the most 11,9MB/s.
Have also tried with an another computer.

What could the solution be?

---

### Post by synapsys on 2009-06-13
Use something other than sftp

---

### Post by orrie on 2009-06-13
> **synapsys said:**
> Use something other than sftp

We tried scp and sftp.

SCP = success
sftp through nautilus = 11,9MB/s
sftp through terminal = 40MB/s and more.


My bad.
Didn't think of that before.... now :P

---

