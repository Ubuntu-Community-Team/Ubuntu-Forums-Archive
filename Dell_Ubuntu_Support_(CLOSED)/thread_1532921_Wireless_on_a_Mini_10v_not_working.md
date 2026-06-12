---
title: "Wireless on a Mini 10v not working"
date: 2010-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by el_heffe on 2010-07-17
OK, I have a Dell Mini 10v that I installed 10.04 on and have installed the restricted drivers for the wireless.  Yet, for the life of me I cannot get my wireless to work with my network.  I have it working enough to recognize the wireless networks, but I have to use a static IP in order for the internet to work.  It's a long story, but basically it goes like this- in order to share the network from my Win7 to work I have to use static IPs.  

So, when I get connected to the network I can assign the IP and everything as such:  192.168.4.3/255.255.252.0/192.168.4.1
But when I go to check it out a couple of things happen which confused me.
It is not wlan0 it is eth1.  It shows the ip as: 192.168.4.1
The weird part is the Bcast is 192.168.7.255 and the Mask is 255.255.252.0.

So, I am not sure what I am doing wrong, but it confuses the hell outta me.  Then when I 
```

$ sudo ifconfig eth1 broadcast 192.168.4.1 
```
it takes, but still doesn't work.  
So then I take it down and back up with 
```

$ sudo ifconfig eth1 down
$ sudo ifconfig eth1 up 
```
Once it does that still no dice.  
```

$ ping 10.5.48.1
connect: Network is unreachable

```

What am I doing wrong?  What would be helpful?  I have an actual ethernet connection that I can use, I would just prefer to have the wireless working so I not have to keep switching back and forth.

---

### Post by snowpine on 2010-07-17
It's a bug. :( I'd suggest following this tutorial to get your wifi working: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

---

### Post by el_heffe on 2010-07-17
My bad, forgot to mention that I downloaded and installed that already.  I have followed that link as well as 

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

Man, there is another site I went to and now I can't find it.

---

### Post by el_heffe on 2010-07-18
OK, still not working, update my kernel, reinstalled bcmwl-kernel-source just in case, followed this site:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Nothing.  Well, sorta.  Now when I ping the gateway 192.168.4.1 it says
```

PING 192.168.4.1 (192.168.4.1) 56(84) bytes of data.
From 192.168.4.3 icmp_seq=1 Destination Host Unreachable

```

This is with the broadcast still at 192.168.7.255.  Any help is much appreciated, it just works when I boot to my Hackintosh side, and I thought the same would be true for Ubuntu after having used the newest version...

---

