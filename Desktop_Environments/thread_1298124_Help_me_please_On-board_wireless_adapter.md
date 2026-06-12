---
title: "Help me please On-board wireless adapter"
date: 2009-10-22
forum: Desktop Environments
---

### Post by tanwa1234 on 2009-10-22
I have a problem with wireless connection.
 First i use motherboard  ASUS M2N32 SLI Deluxe with onboard wireless.
I use Ubuntu in version8.
It can detected my wireless adapter but signal is very very weak.
and another my PC use Ubuntu version8 too but use USB wireless adapter
signal is very strength.


Does Ubuntu  have problems with on-board wireless adapter ?
please help me

---

### Post by undecim on 2009-10-22
If you can see your wireless access point, but jsut have bad reception, then the problem is the hardware, not the software. It may also be that the signal is stronger than is reported.

Try pinging your router from each computer and see if there is a large difference in the numbers reported:
Assuming your router's IP address is 192.168.1.1, run this in a terminal:
```
ping 192.168.1.1
```After a minute or so, press ctrl+C to stop it, and you will get something like this: ```
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 5.690/6.105/7.689/0.794 ms
```Look at the % packet loss, and the average time, and see if there is a major difference between the two wireless adapters

---

