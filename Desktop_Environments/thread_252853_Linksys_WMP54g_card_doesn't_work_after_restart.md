---
title: "Linksys WMP54g card doesn't work after restart"
date: 2006-09-07
forum: Desktop Environments
---

### Post by BirdZerk on 2006-09-07
I have a Linksys WMP54g card (Broadcom 4306) that I got working using the bcm43xx-fwcutter method.  When I reboot the computer the card is no longer working, I have to disable the connection and enable the connection again for the card to start working again.  Is there a fix to this problem?

---

### Post by AZzKikR on 2006-09-07
Take a look at the file /etc/network/interfaces. 
Perhaps, if you append these lines to that file it might work after a reboot:

```
auto [interface_name]

pre-up ifconfig [interface_name] up
pre-up ifconfig [interface_name] down
pre-up ifconfig [interface_name] up

```

This seems to work for my Linksys WMP54G card (although I have the RT2500 chipset). For instance, this is what my configuration file says:

```

<snip other parts not relevant for this post>

auto ra0

iface ra0 inet static
address 192.168.1.7
netmask 255.255.255.0
gateway 192.168.1.1
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "ssid"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="password"
pre-up ifconfig ra0 up

```

---

