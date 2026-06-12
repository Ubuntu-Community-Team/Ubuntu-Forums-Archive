---
title: "Quick router Problem"
date: 2009-05-29
forum: General Help
---

### Post by Jae99 on 2009-05-29
Hello I am new to Ubuntu and I have a quick question about router settings. When I connect directly to my cable Internet  ubuntu works fine. But when I connect it to my router I can't get connectivity. I am using ubuntu 9.04 and am using D-link DI-604 router. I have reset both my router and modem but nothing changed. My ipconfig gives me this

eth0      Link encap:Ethernet  HWaddr 00:1d:92:a4:ec:f3  
          inet addr:99.229.168.96  Bcast:99.229.169.255  Mask:255.255.254.0
          inet6 addr: fe80::21d:92ff:fea4:ecf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4360408 (4.3 MB)  TX bytes:978386 (978.3 KB)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:936 (936.0 B)  TX bytes:936 (936.0 B)

Thanks in advance for any help.

---

### Post by TransitMan on 2009-05-30
Can you access the GUI in the D-Link router?
Do you know the IP address of the D-Link? If so, go to your Network Manager and make the settings manually.
Give the computer a static IP address, with the gateway the router IP.
For DNS use the router IP.
Save this, close and reboot.
Upon reboot you should be able to get online with out issue.

---

