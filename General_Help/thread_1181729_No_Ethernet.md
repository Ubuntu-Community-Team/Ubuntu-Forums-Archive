---
title: "No Ethernet"
date: 2009-06-08
forum: General Help
---

### Post by spydamans on 2009-06-08
I am running ubuntu 8.10 and i was looking for some wireless programs in synaptic to install to check out, something like net-stumbler. So I added a few wireless apps that i later deleted, and all of a sudden my eth0 and eth1 have disappeared and i cant get internet anymore. The eth0 and eth1 stopped working when i installed the wireless apps. I then deleted them and restarted and still no ethernet adapters. Any one know how to reinstall adapters? Thanks in advance for any help.

---

### Post by spydamans on 2009-06-08
Nobody can help with this? It would be greatly appreciated if someone could help.

---

### Post by Idefix82 on 2009-06-08
Please open the terminal, type in
```
lshw -C network
```
and post the output here.

And next time, please wait for at least 24 hours before bumping a thread.

---

### Post by spydamans on 2009-06-08
Thanks for the response, sorry I didnt know there was a wait time. I will keep that in mind for the next time.

---

### Post by Krupski on 2009-06-08
> **spydamans said:**
> I am running ubuntu 8.10 and i was looking for some wireless programs in synaptic to install to check out, something like net-stumbler. So I added a few wireless apps that i later deleted, and all of a sudden my eth0 and eth1 have disappeared and i cant get internet anymore. The eth0 and eth1 stopped working when i installed the wireless apps. I then deleted them and restarted and still no ethernet adapters. Any one know how to reinstall adapters? Thanks in advance for any help.

Try this:

Go into "/etc/udev/rules.d".

Edit the file "70-persistent-net.rules".

You will see one or several lines that look like this:

```

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:c0:21:d0:e4", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

REMOVE all of them, leaving ONLY the comment header on top.

Now, reboot. This will force UDEV to rescan all of your hardware and add your CURRENT NIC as "eth0".

This is also the solution to a common problem where someone has a working system and either replaces the motherboard or replaces the network adapter card. The MAC address changes and UDEV tries to link "eth0" to the *old* MAC address, which of course fails. Result... no network connectivity.

Removing the entry(s) from "70-persistent-net.rules" forces the system to link eth0 to the CURRENTLY WORKING network card.

Lastly, you may wish to make a copy of "70-persistent-net.rules":

```

cp 70-persistent-net.rules 70-persistent-net.rules.original

```

...just in case you need to revert back.

Good luck!

-- Roger

---

### Post by spydamans on 2009-06-10
> Please open the terminal, type in
Code:

lshw -C network

and post the output here.

Here is the output from lshw -C network

 *-network:0 DISABLED    
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:01:6c:2f:05:21
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 10
       serial: 00:08:54:d8:7a:c1
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:cf:30:cb:f5:d3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by spydamans on 2009-06-10
> Krupski

I tried removing the entries but they just got re added to the file, and the ethernet adapters are still not working. Thanks for the response.

---

### Post by spydamans on 2009-06-10
I was talking with someone at work and they suggested that i install the network manager, that is no longer installed. Does anyone know how to install this from the live cd or download it manually?

---

### Post by spydamans on 2009-06-11
anything new?

---

