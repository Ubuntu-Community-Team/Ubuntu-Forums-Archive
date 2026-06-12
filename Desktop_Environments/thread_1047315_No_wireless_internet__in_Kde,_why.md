---
title: "No wireless internet  in Kde, why?"
date: 2009-01-22
forum: Desktop Environments
---

### Post by oblador on 2009-01-22
Hi, I'm running Ubuntu 8.10 and I've installed Kde, but when I try  to access my wireless internet nothing happens. Why can't I have wireless internet in KDE?

Thanks.

---

### Post by XanTrax on 2009-01-22
> **oblador said:**
> Hi, I'm running Ubuntu 8.10 and I've installed Kde, but when I try  to access my wireless internet nothing happens. Why can't I have wireless internet in KDE?

Thanks.

You're going to need to give us some more information.  

1.) Is your card recognized?
2.) Is your card configured?
3.) Does (KDE's version of..) network manager show wireless connections BUT it doesnt connect?


Please open a terminal and type

```

lshw -C network

```

and paste the output please.

---

### Post by oblador on 2009-02-03
my wireless works perfectly on Gnome, but it's not working on KDE... I typed the command (lshw -C network), and that's what was displayed:

WARNING: you should run this program as super-user.
  *-network                                        
       description: Ethernet interface             
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:c9:f9:34:a7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/Alatency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:68:c4:62:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yeswireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:e7:44:30:21:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by abn91c on 2009-02-03
did you right click on the green globe in the bottom toolbar and selected new connection?

---

### Post by oblador on 2009-02-04
yes, it even shows the right wireless network to connect to, but it just doesn't connect.

---

### Post by abn91c on 2009-02-04
just double check your passkey and WPA settings, also in the network wizard make sure you check the Auto connect box under the SSID

---

### Post by oblador on 2009-02-06
I've done it, but nothing seems to work. In Gnome wireless is perfect.

---

### Post by oblador on 2009-02-21
For those who have the same problem, the solution is to install wicd. It runs both in Gnome and KDE without creating conflicts.

---

### Post by ZootHornRollo on 2009-04-07
is it possible to have wicd run in KDE and Network Manager run in Gnome?

i want to switch to KDE but have been having problems trying to get my wireless connected (works flawlessly in Gnome).  I have tried wicd before in Gnome and it caused nothing but problems.

---

