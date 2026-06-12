---
title: "Unable to connect to internet after update"
date: 2009-02-12
forum: General Help
---

### Post by fishscale on 2009-02-12
I am unable to connect to the internet in Ubuntu Intrepid even though I can connect fine in Vista on the same computer.  I blindly updated through update manager (stupid, I know), and I'm not sure what update caused this.  There may have been a kernel update, but I can't be certain.  

I have an Intel 82566DC-2.  I have read a couple of threads on this card, but I get the feeling that this isn't the problem.  I have also tried restarting with an older kernel, and that hasn't worked either.  I read a thread that said
```

sudo shutdown -r now 
```
would work, but it didn't do anything for me.  If it provides any hints, my AWN dock is now missing an applet (although this could be due to the lack of connection, as it is the weather applet).  Instead, it has a place marker where the applet once was.

I spent a long time updating Vista today, as I haven't been on it for a while.  This only reinforced my desire to get back to Ubuntu.  Anyone have any ideas?  I will boot back into Ubuntu and print the output of lhsw and ifconfig.  Any help would be greatly appreciated, thanks.

---

### Post by Peter09 on 2009-02-12
Yes - we need to understand the H/W you've got so yhe outputs would be good.

---

### Post by fishscale on 2009-02-12
```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: [REDACTED]
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.9-2 ip=192.168.15.100 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REDACTED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

```
ifconfig
eth1      Link encap:Ethernet  HWaddr [REDACTED]
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe2b:7a75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:8689 (8.6 KB)  TX bytes:1152 (1.1 KB)
          Memory:f9dc0000-f9de0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:390 errors:0 dropped:0 overruns:0 frame:0
          TX packets:390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23784 (23.7 KB)  TX bytes:23784 (23.7 KB)
```

```
dmesg | tail -n10
[   31.160592] NET: Registered protocol family 10
[   31.161252] lo: Disabled Privacy Extensions
[   34.412457] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   35.900867] 0000:00:19.0: eth1: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   35.900872] 0000:00:19.0: eth1: 10/100 speed: disabling TSO
[   35.901066] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   36.063075] NET: Registered protocol family 17
[   46.796004] eth1: no IPv6 routers present
[  438.372232] usb 8-6.2: reset high speed USB device using ehci_hcd and address 6
[  600.372241] usb 8-6.2: reset high speed USB device using ehci_hcd and address 6
```

---

### Post by fishscale on 2009-02-13
Anything else needed?

---

### Post by Peter09 on 2009-02-13
Are you using DHCP, your subnet mask does not seem to match your IP address.

> eth1      Link encap:Ethernet  HWaddr [REDACTED]
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe2b:7a75/64 Scope:Link


what is the output of 

```
route
```

---

### Post by fishscale on 2009-02-13
Yeah, I don't know why that is.  I am (should be) using DHCP.  Here's the output of route:

```
route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
```

---

### Post by fishscale on 2009-02-13
bump?

---

### Post by Peter09 on 2009-02-14
looks like your gateway is on a different sub-net to your machine.

---

### Post by fishscale on 2009-02-14
How do I fix that?

---

### Post by fishscale on 2009-02-15
Bump?

---

### Post by Peter09 on 2009-02-15
Check /etc/network/interfaces, it should have very little in it if you are using DHCP.

Might be worth checking the configuration of your router.

Right clicking on your network icon will provide motr details under connection information, but it should be the same as ifconfig.

---

### Post by fishscale on 2009-02-16
The file only has two short lines, what else should I check?  I'm pretty sure it's configured to DHCP.  The router seems to be ok since all my other computers are connecting fine.

---

### Post by fishscale on 2009-02-16
bump?

---

### Post by fishscale on 2009-02-17
bump?  anyone?

---

### Post by tsucol11 on 2009-02-17
> **fishscale said:**
> I am unable to connect to the internet in Ubuntu Intrepid even though I can connect fine in Vista on the same computer.  I blindly updated through update manager (stupid, I know), and I'm not sure what update caused this.  There may have been a kernel update, but I can't be certain.  

I have an Intel 82566DC-2.  I have read a couple of threads on this card, but I get the feeling that this isn't the problem.  I have also tried restarting with an older kernel, and that hasn't worked either.  I read a thread that said
```

sudo shutdown -r now 
```
would work, but it didn't do anything for me.  If it provides any hints, my AWN dock is now missing an applet (although this could be due to the lack of connection, as it is the weather applet).  Instead, it has a place marker where the applet once was.

I spent a long time updating Vista today, as I haven't been on it for a while.  This only reinforced my desire to get back to Ubuntu.  Anyone have any ideas?  I will boot back into Ubuntu and print the output of lhsw and ifconfig.  Any help would be greatly appreciated, thanks.

Can you post the lines found in /etc/network/interfaces

Brian

---

