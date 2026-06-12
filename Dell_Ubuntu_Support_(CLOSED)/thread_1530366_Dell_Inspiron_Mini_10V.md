---
title: "Dell Inspiron Mini 10V"
date: 2010-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sillyrabbit008 on 2010-07-13
Hi,

I have a Dell Inspiron Mini 10V (Ubuntu 10.0.4 LTS) with a Broadcom BCM4312 Wifi card. I have installed the "Broadcom STA wireless driver" and in the Hardware Drivers system application it says "This driver is activated and currently in use." When I click on the wireless icon at the top I get a list of nearby wireless networks, so I am assuming that the system recognizes the wifi card and it is working to some degree. The problem is when I try to connect to a wireless network (either WEP or WPA/WPA2), it either won't connect or will connect but I can't access the internet. I can't even ping the wireless router (IP address 192.168.1.1).

The /etc/network/interfaces file contains the following:

auto lo
iface lo inet loopback

Should a DHCP entry also be in there? Should eth1 be in there too? The wired ethernet card is eth0 and the wireless card is eth1. The wired ethernet card is working fine when I manually connect to it by clicking on "auto eth0." But the wireless is not working. Even when it says it is connected to the wireless network I can't access the internet. I've looked around for a few hours on the forums and could not find an answer to this problem. I am a relative newcomer to Linux, but I've read that using Broadcom wireless cards with Linux is not so easy to set up. Can anyone point me in the right direction? Thank you in advance.

Akito

---

### Post by Megaptera on 2010-07-13
Hi,
Have you tried this? It's worked for me on my Dell in 9.10 and 10.04

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

Don't forget to reboot though.

---

### Post by mikewhatever on 2010-07-14
When it says it's connected, can you post the outputs of the following:
```

nm-tool

```
The interfaces file looks ok, there is no need to add anything.

---

