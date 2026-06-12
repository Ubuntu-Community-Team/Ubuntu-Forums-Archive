---
title: "connection sharing"
date: 2005-04-24
forum: Desktop Environments
---

### Post by Renato Souza on 2005-04-24
I have a pc with 2 netcards eth0 is conected to a adsl modem (pppoe) eth1 is conected to another pc with a crossover cable. the lan conects at 10 mbit/s ive tried sharing the conection through firestarter but it didnt work. Can somebody please give me a tutorial to route the conection to my other pc

---

### Post by kkith on 2005-04-24
[QUOTE=Renato Souza]I have a pc with 2 netcards eth0 is conected to a adsl modem (pppoe) eth1 is conected to another pc with a crossover cable. the lan conects at 10 mbit/s ive tried sharing the conection through firestarter but it didnt work. Can somebody please give me a tutorial to route the conection to my other pc[/QUOTE]

You are trying to perform packet forwarding also known as NAT.  I'm unsure what firestarter is (sounds like a front end to iptables), but iptables is what you need.  If you are using a stock kernel, I am guessing the kernel has been already compiled for packet forwarding.

It is all here, admittedly I have not read this particular tutorial, but a cursory glance leads me to believe all the information you need is right here:

[http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

If you still can't figure it out from the tutorial, I can post my iptables rules and you can probably make some modifications to the rule-set specific for your system.

Good Luck.

---

### Post by fipeso on 2005-04-24
I dont know if this helps, but I too have 2 PC where one PC has 2 NIC, that I just have set up.

Im a newbie on Linux and Ubuntu, so this might not be correct info tho...

On the server eth0 is connected to adsl modem and eth1 is connected to a switch, so its almost the same as your setup.

I could not get this to work with firestarter. I also had huge problems to even get the PC with 2 network cards connected to the Internet correctly.
(The network settings in Ubuntu would not set default gateway to eth0 :()

But as I am a newbie, that has used M$ for 15 years, I did some basic errors :)

I assumed that Firestarter would setup a DHCP for me on the internal LAN.
I assumed that Firestarter would setup routing correctly automatically.
This is somthing that might work on XP connection sharing, but not here. 

So I first uninstalled Firestarter, to make sure it does not mess up things at this point.

I set eth0 for DHCP and set a manual IP for eth1 (10.0.0.1)

Then I had to use "route del ..." and "route add ..." commands to get the PC with 2 NIC's to get on the internet correctly. (It wanted to go on the LAN side for Inet)
(There was 2 default routes(?) so I deleted them and added the ISP router as default on eth0)

Then I installed "Shorewall" with apt-get, and followed the "2 nic how to"
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

And finaly I had to set on the LAN PC manual ip addresses (10.0.0.2) and manual DNS (from ISP) and set the 10.0.0.1 as default gateway.

I dont know if this was the "right" way to do this, but it works  :-P 

Next step would be setting it up so that LAN pc's can use 10.0.0.1 as DNS, and then I might want to setup a DHCP server on 10.0.0.1.

If a Linux guru reads this, I hope they comment if this is all wrong  O:) 

PS.
This is how my routing looks like on the "fw" pc:
```

peter@fw1:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
217.140.240.0   *               255.255.240.0   U     0      0        0 eth0
10.0.0.0        *               255.0.0.0       U     0      0        0 eth1
default         217-140-240-1.a 0.0.0.0         UG    0      0        0 eth0

``` 
I dont know if this is correct, and why the format for default looks so strange  :???: 
But it works  \\:D/

---

