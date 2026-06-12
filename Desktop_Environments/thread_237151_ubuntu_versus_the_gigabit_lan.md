---
title: "ubuntu versus the gigabit lan"
date: 2006-08-15
forum: Desktop Environments
---

### Post by mykrob on 2006-08-15
Hey-

a friend just called.. He just installed a file server for a local paving company. The server is an older HP Pavlion, i think it is about 500MHz, maybe 433.. not important.. The OS inquestion is Ubuntu Server 6.06, running the XFCE desktop. It has installed Samba, SWAT, and Webmin.. It worked fine when i set it up at my place. However, when he got it, he removed the ethernet card it had and installed a newer Linksys Gigabit LAN card. He called to say that the card is showing in the console using lspci, but apparently is not set up, because when he runs ifconfig, the only device showing is the local loopback device...

I will have him chime in later today with whatever specifics you need, but just on initial glance, do any of you know why a simple ehternet card would not work right out of the box?

Thanks,
-myk

---

### Post by ciscosurfer on 2006-08-15
This following page is helpful: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

As an aside, unless this company is sending enormous amounts of data at once, having Gigabit to the desktop is useless -- and will be limited by the server that it's connected to, i.e., a 500 Mhz machine can't process info that fast anyway...my point is that your bottleneck will occur on the machine itself, not necessarily on the network.  Servers with Gigabit that connect to local SAN's, etc., with Gigabit, will benefit from this.  But in general, a FastEthernet card will do the trick.  Just my 2 cents.

---

