---
title: "Poweredge 2950 network not working - hardy"
date: 2008-05-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chadersberger on 2008-05-28
I just rebuilt a Dell Poweredge 2950 that was running a beta of Ubuntu Hardy Server with the released version of the OS.  Now I cannot get network connectivity from eth0.  I have tried using DHCP and also assigning a static address to the interface but neither work.  DHCP requests fail to find the DHCP server on my network and if I use a static address I cannot ping anything on the network.  The Dell is using an onboard Broadcom NIC and everything worked properly before so I don't think it is hardware or infrastructure related and I do see activity lights on the NIC and the switch.

---

### Post by barichardson5727 on 2008-05-28
Make sure the NetXtremeII module is loaded:
```
lsmod | grep -i bnx2
```

Are you configuring the network interfaces from the NetworkManager or directly in the config files? If directly editing the config files post the configuration.

---

### Post by chadersberger on 2008-05-29
I am working directly with the files (I do not have a GUI installed).
Here is the interfaces text:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

And here is the result of an ifconfig command:

eth0      Link encap:Ethernet  HWaddr 00:19:b9:ea:2a:8c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f4000000-f4012100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

---

### Post by barichardson5727 on 2008-06-01
Have you tried configuration on BOTH adapters on the server? Try adding the second adapter to the configuration file as eth1 and running dhclient. Sometimes the physical network adapters will switch between eth0 and eth1 if you do not bind them to the mac address with the HWADDR= entry in the config files. Also, when you are trying to ping are you using the ip address or the host name?

---

