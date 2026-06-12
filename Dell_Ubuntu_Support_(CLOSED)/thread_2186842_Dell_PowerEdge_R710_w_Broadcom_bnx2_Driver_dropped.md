---
title: "Dell PowerEdge R710 /w Broadcom bnx2 Driver dropped RX packets"
date: 2013-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by autogun on 2013-11-09
Hello Community,

Im running two similar Dell PowerEdge R710 servers with Broadcom Corporation NetXtreme II BCM5709 Gigabit Ethernet (rev 20),
Running Ubuntu 12.04.3 LTS with 3.8.0-33-generic kernel.
```
driver: bnx2
version: 2.2.3
firmware-version: 6.2.12 bc 5.2.3 NCSI 2.0.11
bus-info: 0000:01:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
```

ifconfig reports dropped RX packets
```
eth0      Link encap:Ethernet  HWaddr d4:ae:52:6e:07:81
...
...
          RX packets:117503 errors:0 dropped:33436 overruns:0 frame:0
          TX packets:89998 errors:0 dropped:0 overruns:0 carrier:0

```

I've changed physical cables, checked switch for errors. Problem not there.

What am I missing?

Appreciate your help!

---

### Post by prshah on 2013-11-09
Are your servers configured for ipv6? ipv6 frames received when the server is not configured for ipv6 go to the dropped packets counter.

A quick way to check if the frames are legitimate drops is to run tcpdump in another terminal, and then watch the counter; if the counter continues to increment, then there is an actual fault that needs to be resolved.

Are you facing any symptoms with your network, or just concerned about the dropped packet count?

---

### Post by tgalati4 on 2013-11-09
If your server has dual ethernet ports, try using the other port.  How old are these machines?  It could simply be chip failure on the motherboard.  How many power-on hours?

```
sudo smartctl -a /dev/sda | grep Power
```

---

### Post by autogun on 2013-11-10
Hi,

Thank you for the answers,

I've disabled ipv6 support running these commands, did **not **help -
```
sysctl -w net.ipv6.conf.all.disable_ipv6=1
sysctl -w net.ipv6.conf.default.disable_ipv6=1
sysctl -w net.ipv6.conf.lo.disable_ipv6=1
```

Reading all around the web, this is some kind of a known issue with Broadcom Ethernet cards but non talking about my driver version, only older once.

Im not facing symptoms yet but servers are not yet in production, Im afraid to go live while this issue present.

Pardon me,
Maybe this thread fits better to Server Platforms forum

---

### Post by autogun on 2013-11-12
Nagging a few to the DataCenter engineers where two of the servers are hosted brought a fix, well, nothing was actually broken.
Following [this ]("http://www.novell.com/support/kb/doc.php?id=7007165")technical KB by Novell, it's seems this behavior is by design in kernel > 3.x
bpdufilter was configured on both switch ports servers were connected to and dropped packets are gone now.

Yay!

EDIT: I still believe this thread belongs to Server Platforms forum :)

---

