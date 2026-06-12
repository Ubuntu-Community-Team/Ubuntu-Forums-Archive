---
title: "530n network card stopped working in 8.10"
date: 2008-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by satbunny on 2008-11-04
Sigh. I upgraded to 8.10 this afternoon on my Dell Inspiron 530n, having done so on my Thinkpad laptop.

I have rebooted and Ubuntu no longer talks to my network card/or possibly the network.

Is this a known problem, is there a fix? I have trawled the ppp.launchpad.net archive but the firmware stuff there is for gutsy and anyway it needs an Internet connection to install.

Help?

---

### Post by nostarch on 2008-11-06
I had a similar problem. Try:

> sudo dhclient eth0

---

### Post by satbunny on 2008-11-06
I have trekked back to 7.10 and then up to 8.04. All works fine in these releases.
I shall boot off a LiveCd later and do as you say, do you want the results or is it a solution?

---

### Post by satbunny on 2008-11-09
Ok.

When I boot from a 8.10 LiveCD then the network manager fails to connect automatically and if I set it up manually it also fails to talk to my server.

When I run dhclient eth0 I get:

> Listening on LPF/eth0/00:1a:a0:9d:20:7b
Sending on  LPF/eth0/00:1a:a0:9d:20:7b
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping

When I boot my 8.04 install and run dhclient eth0 I get:

> There is already a pid file /var/run/dhclient.pid with pid 6355
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:a0:9d:20:7b
Sending on   LPF/eth0/00:1a:a0:9d:20:7b
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.126 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.126 from 192.168.2.1
bound to 192.168.2.126 -- renewal in 42967 seconds.


Not sure where to go from there..

---

### Post by Charter33 on 2008-11-09
Hi,
 don't know if this is relevant, but I couldn't get my wireless card working in 8.10 (fine in 8.04).  The Network Manager couldn't separate my card from the built-in Intel wireless, and I had slow start-ups and a general mess trying to configure the hardware and the network settings.
  
 I  have now uninstalled Network Manager, and gone back to using network-admin.  8.10 is now running well with my wireless card.

---

### Post by satbunny on 2008-11-10
Thanks. I think that since dhclient is failing then it is lower than Network Manager but I shall try again with a LiveCD, uninstall NM and see what happens.

---

### Post by satbunny on 2008-11-23
Ok, it seems to have been a duff LiveCD.
I tried to run terminal and it failed. 
So I downloaded a new iso, burnt it, booted it and my network worked fine. Upgraded and 8.10 fine.

I have never had a duff iso before so that's a lesson, eh?

Mind you, it taught me to learn how to use Clonezilla so I now have a totally backed up image of my 8.04 install!

:)

---

