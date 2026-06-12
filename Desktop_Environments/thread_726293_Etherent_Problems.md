---
title: "Etherent Problems"
date: 2008-03-16
forum: Desktop Environments
---

### Post by haveacigar on 2008-03-16
Im trying to set up a home server, so I can learn a bit of the unix syntax and be able to share files through our local network. However I seem to be having a problem, and cannot get the ethernet port to work....

It seems to be recognised by ubuntu (7.10) but when i connect it to another computer it always says "no cable connected". Its direct computer to computer so im using a crossover cable...

Any help woudl be much appreciated, as i would rather use an ubuntu server than the windows home server.

Thanks

Ciggy

---

### Post by louieb on 2008-03-16
1st thing I would do is see if Ubuntu sees your NIC. 
Applicatations>Accessories>terminal
```
ifconfig 
```
if all is well you should see two entries one labeled **eth0** or maybe **eth1** or some other #. This would be the entry for your NIC.

The other entry will be labeled **lo  **this is the loopback entry used for letting that pc talk to itself.  

Seems to me that one or the other computer would have to act as a DHCP server. or you would need to set up both PC's to use a static IP.

Haven't used a crossover cable in years forgot how.

---

### Post by thinkdez on 2008-03-17
There should be no special requirements for a x-over cable.  I have to agree with louieb in that if you haven't set a static IP address for the server and the host machine then you will need a DHCP server on one of the machines.  

One thing that may also be happening is that your ethernet device may not be recognized by ubuntu.  Hard to imagine that you would have an chipset that would do this but also checking to see if your system recognizes it  run the following command:

```
#sudo /sbin/lspci
```

You should get output of all the devices on the system and one should look similar to the following:

```

00:07.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)

```

Yours should differ in respect to your Ethernet adapter.

Although this I still believe your problem lies with IP assignment of both the server and host.

Hope that helps

---

