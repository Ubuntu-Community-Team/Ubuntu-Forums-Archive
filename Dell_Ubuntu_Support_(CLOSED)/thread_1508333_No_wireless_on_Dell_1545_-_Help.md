---
title: "No wireless on Dell 1545 - Help"
date: 2010-06-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kashifmehmood on 2010-06-12
Hello,

I had wrecked my previous installation of Ubuntu 10.04 by fiddling with the wireless setup. I tried everyting (ndiswrapper, linuxwireless.org, hardware drivers option in ubuntu) but nothing worked. 

I formatted my HD and installed a fresh copy of Ubuntu 10.04 LTS 32-bit. Running the following command:

lspci -vnn | grep 14e4

gave the output "14e4:4315". As I understand this chip is supported by b43 driver, I installed the b43 driver via Administration/Hardware drivers.

Now, after a couple of restarts, it is still not connecting to wireless, with various issues. 

-Sometimes no wireless networks are detected. 
-After a couple of restarts, it detects the wireless but fails in authentication (I have several other devices attached to the router and know the password I am giving is correct).
-In other scenarios, it would try to connect (and both of the network connection "lights" on the status icon would light up) but then it would say "disconnected".

Please help as I am at my wits end. I have not made any changes to the fresh ubuntu setup aside from installed the b43 driver.

Many thanks in advance.

---

### Post by c0brabg on 2010-06-13
I am with dell 1525 and I am using Broadcom STA wireless driver. I think that we both have the same wi-fi card, never the less : [http://www.vglug.info/forums/vglug-discussion/how-configure-dell-1545-wireless-card-fedora-12-or-linux-solved](http://www.vglug.info/forums/vglug-discussion/how-configure-dell-1545-wireless-card-fedora-12-or-linux-solved) 
Follow the instructions carefully and you should be OK !

---

