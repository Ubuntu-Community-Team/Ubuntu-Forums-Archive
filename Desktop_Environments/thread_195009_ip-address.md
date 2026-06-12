---
title: "ip-address"
date: 2006-06-12
forum: Desktop Environments
---

### Post by skipo on 2006-06-12
I don't get an ip-address untill I restart the ethernet interface. How can I get an ip-address automatically?

---

### Post by rbalfour on 2006-06-12
[QUOTE=skipo]I don't get an ip-address untill I restart the ethernet interface. How can I get an ip-address automatically?[/QUOTE]

Can you post your /etc/network/interfaces file?

---

### Post by skipo on 2006-06-12
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by rbalfour on 2006-06-12
[QUOTE=skipo]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp[/QUOTE]

Can you check to see if this works?

$ sudo /etc/init.d/networking start

---

### Post by jvictor on 2006-06-12
Instead of relying n DHCP use a static IP if possible

---

### Post by skipo on 2006-06-12
If I type

$ sudo /etc/init.d/networking restart

I get an address, but that's really not the answer to my question, because I'd like to get the address _automatically_

---

### Post by nvbauer on 2006-06-12
Did you install from the Dapper final ISO or did you upgrade. I had this problem whe I installed from Flight-6 on through and after final release. I finaly reinstalled today from the Final ISO and everything seems to be ok now.

---

### Post by skipo on 2006-06-13
I installed it from the ISO. I'll probably try the reinstalling next.

---

### Post by frup on 2006-06-13
on breezy DHCP didnt work for me... so i just use static.. not to sure if its cos my routers funny

---

### Post by rbalfour on 2006-06-13
[QUOTE=skipo]If I type

$ sudo /etc/init.d/networking restart

I get an address, but that's really not the answer to my question, because I'd like to get the address _automatically_[/QUOTE]

so you are half-way there.

either.
1) the network card isn't found when networking service starts. ie. networking fails on boot

2) the networking service isn't starting when booting.

Watch the boot process and see if the system is booting the NIC properly.

$ dmesg
really helps/.

---

### Post by skipo on 2006-06-13
There wasn't any failures in boot process, even the network interfaces configured ok, but ifconfig gave this kind of report:

eth0    
Link encap:Ethernet  HWaddr 00:13:D4:9A:B3:E0
          inet6 addr: fe80::213:d4ff:fe9a:b3e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:5 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:185

So I'm thinking that the NIC is found but the networking service didn't start.

How can I start it when booting?

---

### Post by skipo on 2006-06-15
Problem solved, I reinstalled the system. Thanks for help, I really appreciated it.

---

### Post by skipo on 2006-06-17
Ok, reinstalling the system didn't really helped at all, but I installed network-manager, that seems to be working.

---

