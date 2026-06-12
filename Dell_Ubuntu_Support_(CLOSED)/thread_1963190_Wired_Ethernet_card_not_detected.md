---
title: "Wired Ethernet card not detected"
date: 2012-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by olimak on 2012-04-22
I have installed Ubuntu 10.04 on a Dell Optiplex 990 desktop, dual-booted with Win7. There is no network connection on Ubuntu, tho it works under Win7.
 
Here are some results from Terminal:
 
========================
**ifconfig -a**
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:140 errors:0 dropped:0 overruns:0 frame:0
TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:10960 (10.9 KB) TX bytes:10960 (10.9 KB)
 
**lspci -nn**
00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04)
 
**lshw -C network**
WARNING: you should run this program as super-user.
*-network UNCLAIMED 
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:e1a00000-e1a1ffff memory:e1a80000-e1a80fff ioport:3080(size=32)
 
========================
 
Perhaps it is the case that no driver is present for this network card in 10.04. I did download the file e1000e-1.10.6.tar.gz from Intel (for the Intel 82574LM network card = VEN_8086, DEV_1502), but I'm not sure it's what I need, nor do I know how to install it to try, or for that matter, how to uninstall it if I need to.
 
Thanks!

---

### Post by sanderj on 2012-04-22
If you live-boot from CD (or USB) Ubuntu 11.10 or 12.04 (=beta), what's the output of those commands?

---

### Post by olimak on 2012-04-22
> **sanderj said:**
> If you live-boot from CD (or USB) Ubuntu 11.10 or 12.04 (=beta), what's the output of those commands?
 
The card works with 12.04:
 
====================
 
**sudo ifconfig -a**
eth0 Link encap:Ethernet HWaddr 78:2b:cb:97:91:54 
inet addr:192.168.0.9 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::7a2b:cbff:fe97:9154/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:478 errors:0 dropped:0 overruns:0 frame:0
TX packets:392 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:313598 (313.5 KB) TX bytes:52001 (52.0 KB)
Interrupt:20 Memory:e1a00000-e1a20000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:66 errors:0 dropped:0 overruns:0 frame:0
TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:6348 (6.3 KB) TX bytes:6348 (6.3 KB)
 
**lspci -nn**
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
 
**lshw -C network**
WARNING: you should run this program as super-user.
*-network 
description: Ethernet interface
product: 82579LM Gigabit Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 04
serial: 78:2b:cb:97:91:54
size: 1Gbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=192.168.0.9 latency=0 multicast=yes port=twisted pair speed=1Gbit/s
resources: irq:41 memory:e1a00000-e1a1ffff memory:e1a80000-e1a80fff ioport:3080(size=32)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
 
====================
 
Thanks for help.

---

### Post by sanderj on 2012-04-22
> **olimak said:**
> The card works with 12.04:
 
<snip>
 
Thanks for help.

OK, good. Apparently your network hardware is newer than Ubuntu 10.04.

So ... problem solved?

---

### Post by olimak on 2012-04-22
> **sanderj said:**
> OK, good. Apparently your network hardware is newer than Ubuntu 10.04.
 
So ... problem solved?
 
 
Rationale: I'm implementing FOGProject for an imaging application. FOG is known to work with 10.04 ([http://www.fogproject.org/wiki/index.php?title=Installation).](http://www.fogproject.org/wiki/index.php?title=Installation).) I thought it would be more straightforward to use that version and install any extra driver needed, rather than embark on qualifying/debugging FOG in a more recent environment. After all, 10.04 is LTS until next April. Still looking for the steps to install the driver, thanks.

---

### Post by sanderj on 2012-04-22
OK, clear.

Maybe this thread helps: [http://ubuntuforums.org/showthread.php?t=1741686&page=2](http://ubuntuforums.org/showthread.php?t=1741686&page=2)

---

### Post by olimak on 2012-04-23
> **sanderj said:**
> OK, clear.
 
Maybe this thread helps: [http://ubuntuforums.org/showthread.php?t=1741686&page=2](http://ubuntuforums.org/showthread.php?t=1741686&page=2)
 
I took a peek in the desktop case and found a spare PCI slot, put in an old network card that was successfully recognized by 10.04, so now I have network access on one port, ok for now. I'll return to the other driver later. Thanks for help.

---

### Post by sanderj on 2012-04-23
> **olimak said:**
> I took a peek in the desktop case and found a spare PCI slot, put in an old network card that was successfully recognized by 10.04, so now I have network access on one port, ok for now. I'll return to the other driver later. Thanks for help.

That's a very pragmatic solution! The same way I would do it! :p

---

