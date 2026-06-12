---
title: "Virtual box"
date: 2009-08-17
forum: Desktop Environments
---

### Post by nomko on 2009-08-17
I've downloaded and installed Virtual Box for Ubuntu 9.04 (website [www.virtualbox.org]("http://www.virtualbox.org")) but after installing Windows XP i can't install any program in XP. I still need XP with Internet connection for my navigation device (TomTom XL IQ Europe) to update the maps etc.  

Is there anybody who can tell me what the problem is? I'm using 9.04 and not the OSE version of Virtual Box.
Many thanks!

---

### Post by slakkie on 2009-08-17
Could you have a look at your interface configuration:

ifconfig -a should display an entry like this:

```

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And check if you have your vm configured with NAT:
[http://www.euronet.nl/users/wesleys/vbox_network_settings.png](http://www.euronet.nl/users/wesleys/vbox_network_settings.png)

Best of luck!

---

