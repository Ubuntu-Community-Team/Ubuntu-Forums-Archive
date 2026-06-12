---
title: "Home Network Prob"
date: 2006-03-10
forum: Desktop Environments
---

### Post by OffHand on 2006-03-10
Hi all

I would like to set up my Ubuntu pc as a gateway for my Mac.
I tried the guide on the following link but that didn't seem to do the trick.
[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

My situation is the following:

My PC with Ubuntu is connected to the internet using eth0 (the card connected to my modem). It gets it's address with DHCP. So far so good.
Now I got another card, eth1, which is doing nothing atm hehe
My Mac is set to Using DHCP.

Now under System>Administration>Networking eth1 is set to static ip 192.168.0.1 and the subnet to 255.255.255.0
Gateway is empty and the connection is enabled.
If I am trying to run Firestarter (I'm paranoid) it gives me an error and tells me to check my connection. The wizard doesn't help either nor does disabling the Firewall.

Help is greatly appreciated. I know this shouldn't be too hard  :)

P.S. I removed the Firewall to make things easier.

---

### Post by OffHand on 2006-03-10
Got it working with manual IP somehow :)

---

