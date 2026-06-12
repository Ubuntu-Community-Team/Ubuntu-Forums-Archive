---
title: "WakeonLAN Nforce4 bug"
date: 2006-08-09
forum: Desktop Environments
---

### Post by subzero79 on 2006-08-09
Recently i posted that i have been with problems trying to wake up remotely (WOL) my ubuntu box. The problem is that when shutting down from WinXP  i could WOL succesfully with magic packet trough the LAN. On the other side when shutting down from Ubuntu WOL didn't work at all...until today. I have reading that by default the wol isn't enabled in the NIC driver so for that we do "sudo ethtool -s eth0 -g" also adding it as a startup script because everytime it reboots the setting goes away. Doing that didn't work at all...why? because the WOL package has to be sent with the MAC reversed, instead of 01:02:03:04:05:06, it has to be 06:05:04:03:02:01.
Is there a way to fix the ethernet driver(forcedeth) for accepting the correct MAC(not reversed). This is a bug that is discussed here [http://bugzilla.kernel.org/show_bug.cgi?id=6604](http://bugzilla.kernel.org/show_bug.cgi?id=6604)

Athlon64 3200
EPOX 9NPA+ULTRA

thanks

---

### Post by Chris Tucker on 2006-08-11
I have been using "sudo ethtool -s eth0 wol g", perhaps that little - in front of the g is your prob? wild chance though, as running the command with - in front of the g, at least for me, it throws an error at me. Benefit of the doubt, try "sudo ethtool -s eth0 wol g" BY HAND, sudo halt   right after, and attempt to wake via lan again, first with the correct mac, if that fails, try reverse again. Post the results...

---

### Post by subzero79 on 2006-08-11
Sorry for the mispelling of '-'

i've add a startup script at /etc/init.d/ethtool with the following line

ethtool -s eth0 g

so the wol function is enabled every time ubuntu starts. Because this setting  goes away when the system is restarted

the output of "sudo ethtool eth0" gives me

```
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: g
        Link detected: yes
```



Yet i confirm that waking up the computer over the LAN has to be with the reversed MAC when the pc is halted through ubuntu.

---

