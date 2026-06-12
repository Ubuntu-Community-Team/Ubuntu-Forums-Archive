---
title: "eth0 network problem"
date: 2005-11-22
forum: Desktop Environments
---

### Post by tomatchili on 2005-11-22
I have problem getting the network connection to work.

I have tried connection to DI-624+:
The fysical connection seems to work as there is "green ligth" on both sides. 

I tried with DHCP but I do not seem to get any IP adress. If i look in system->networktools (or similar, I have a swedish intallation) I only have an IP v6 IP adress,  no IP v4 adress. I can not ping my router (192.168.0.1)

I have also tried a static IP adress assignement from DI-624 with the same result.

I have also tried without the D-link router,i.e connected to my ADSL modem,

One strange thing is that the "primary networkinterface" seems to reset as soon as close the networkadministration program. When I restart the program no "primary networkinterface" is choosen.

It works on windows and I have got it working before on Linux.(But I have changed harddrive since)

Thankful for help!

---

### Post by dcstar on 2005-11-22
[QUOTE=tomatchili]I have problem getting the network connection to work.

I have tried connection to DI-624+:
The fysical connection seems to work as there is "green ligth" on both sides. 
......[/QUOTE]
In a terminal, do: **ipconfig **and post the results here.

---

### Post by tomatchili on 2005-11-23
I got a strange log when booting the system. When it comes to
"Congifuring network interface:"
it prints out "irq11: nobody cared (try booting with the "irq_poll" option) e.t.c."

Is the network interface driver (or similar) coredumping?

---

### Post by dcstar on 2005-11-23
[QUOTE=tomatchili]I got a strange log when booting the system. When it comes to
"Congifuring network interface:"
it prints out "irq11: nobody cared (try booting with the "irq_poll" option) e.t.c."

Is the network interface driver (or similar) coredumping?[/QUOTE]
Quite possible there is some sort of shared interrupt that is causing the problem.

Can you go into your BIOS and change the network card interrupt to something else?

---

### Post by tomatchili on 2005-11-25
here is the ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:C7:A3:54:25  
          inet6 addr: fe80::208:c7ff:fea3:5425/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:197 overruns:0 frame:0
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:234136 (228.6 KiB)  TX bytes:234136 (228.6 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:57:FD:6F  
          inet6 addr: fe80::20f:3dff:fe57:fd6f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5

---

### Post by dcstar on 2005-11-25
[QUOTE=tomatchili]here is the ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:08:C7:A3:54:25  
          inet6 addr: fe80::208:c7ff:fea3:5425/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:197 overruns:0 frame:0
          TX packets:0 **errors:1** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x2400 
.......[/QUOTE]
I'd say there is a problem with the hardware setup somewhere, see if you can change the IRQ from 11 to something else.

---

