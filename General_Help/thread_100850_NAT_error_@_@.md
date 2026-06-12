---
title: "NAT error @_@"
date: 2005-12-08
forum: General Help
---

### Post by Valcrist on 2005-12-08
Ok I'm not very new to linux, but I'm not nearly an expert either. When using Azerues I'm getting the yellow smiley, therefore a NAT error. 

I've opened the udp and tcp port for it, and I have no firewall installed (that I am aware of), yet when I scan the port it says that its stealthed.

I've installed Sun Java 1.5.

I'm using a Blitzz BWA711S, on Breezy Badger. Thank you for anyone that can help me with this.

---

### Post by zi99y on 2005-12-08
is the blitzz device a router? do you have a wifi router and an adsl router or are they one and the same? you will have to make sure you do port forwarding on both. 

also are you using a static or fixed ip address. you should make sure your ip of your network interface is the same as the one you have setup port forwarding on the router. 

sorry if these sounds straightforward, trying to help in my own small way :D

---

### Post by zi99y on 2005-12-08
also it could be something to do with iptables that might be loading by default. have a look here:

[http://www.ubuntuforums.org/showthread.php?t=87200]("http://www.ubuntuforums.org/showthread.php?t=87200")

---

### Post by Valcrist on 2005-12-08
I'll have to try the iptables thing, but the blitzz device is just a router, my adsl modem is hooked into the wan port (obviously :razz: ). I'm pretty sure I set it to my ip adress (my router sets the first computer connected to it to 192.168.1.2, and the next is 192.168.1.3, and I have a laptop hooked up to it as well so I did both addresses) how do I check my ip adress in ubuntu? (sometimes its the simple things I can't figure out).

---

### Post by zi99y on 2005-12-08
use ifconfig to check your ip address

hmm, I'm not sure but I don't think you can port forward the same ports to two different ip addresses, maybe you should only forward to the actual ip address of your machine, and remove the ones for the ones for your laptop....

---

