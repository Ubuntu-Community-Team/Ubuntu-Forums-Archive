---
title: "WLAN USB stick switches its self off"
date: 2006-03-26
forum: Desktop Environments
---

### Post by satrich on 2006-03-26
I have installed a wireless network. The driver installation of the Ralink rt2570 are installed. It connects, everything looks fine.
But when I start downloading and uploading with aMule the USB stick switches its self off after a period of time. Sometimes the connection lasts for more than an hour, but most of the time it loses connection after a few minutes of havy dataload.
The only thing I can do then, is to pull the usb-stick out and in again, restart the network, and the hole process repeates again.

The hole thing is driving me crazy. I tried different channels, I disabled WEP-encryption, I moved the stick on a better position to get better reception. Nothing helps sofar.

Anyone have any suggestions?

---

### Post by lupine_nickt on 2006-03-26
I've had the same problem for a while now. My bet is that it's to do with the driver not being able to handle all the simultaneous requests. The rt2x00 driver (which is a later version and can't be installed on Breezy because it needs a 2.6.13 + kernel), I think, might solve the problem - but you'll have to compile a custom kernel or upgrade to dapper to get it (which is what I've done). 

I'm actually just starting aMule up right now... I'll let you know in a couple of hours whether it makes a difference or not :)

xF,

...Nick

---

### Post by lupine_nickt on 2006-03-26
Yep, that seems to have done the trick :)

Switch to the rt2x00 beta 3 driver

xF,

...Nick

---

### Post by satrich on 2006-03-26
OK, I will try that. It might take me some time to install Dapper. But i 'll get back to post the result.
Thanks so far.

Richard

---

### Post by satrich on 2006-03-29
OK, I need your help here.
I have installed Ubuntu Dapper. Looks nice...
Then I used my wired ethernet card to update Dapper with the suggested updates.
Then I downloaded the rt2x00 driver. I did the install, and that went bassically ok. After a reboot I disabled the ethernet card, and enabled the wireless usb stick. I select DHCP to connect to the modem/router. I can see that the usb stick on, and there seems to be a connection with the modem/router. 

But whatever I do, I dont't have an internet connection.

When I do a network restart I get these messages, so I guess my installation went fine because I get an IP from the modem:

root@LinuxPC:/home/richard# /etc/init.d/networking restart
 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:02:44:b3:e4:7d
Sending on   LPF/eth1/00:02:44:b3:e4:7d
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.254 port 67
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:02:44:b3:e4:7d
Sending on   LPF/eth1/00:02:44:b3:e4:7d
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.254
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.66 -- renewal in 42025 seconds.


So, my question is: What to do after the installation of the drivers? It's maybe a silly thing, but I am not that experienced in Linux. So, I hope you can help me out here.

---

