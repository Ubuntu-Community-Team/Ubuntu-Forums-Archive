---
title: "gtkwifi broke my wifi connection, now ifup and ifdown dont work"
date: 2005-11-29
forum: Desktop Environments
---

### Post by ren wins on 2005-11-29
edubuntu was giving me too many headaches, wireless internet being one of them
so i uninstalled it and installed ubuntu's breezy badger

wireless internet worked as soon as i fired it up, so i said "hey, this gtkwifi thing may save me lots of headaches in the future!" so i hurried over to the appropriate forum, downloaded it and installed it using the dpkg command (just like what the forum says to do)

i fire it up (gtkwifi run-in-window &) it finds my connection, but does a whole lot of sitting about doing nothing (at least i thought so)

updates to ubuntu had finished installing, as well as the ones from added repositories and backdoors, so i restart my computer
as soon as it fires back up, there's no wifi connection and gtkwifi spends a lot of time searching for something that is clearly there (router working, and my windowsXP laptop can connect to the internet (like right now))
after a couple restarts, i got this error
```
laserwolf@violet:~$ gtkwifi run-in-window &

[1] 11414

laserwolf@violet:~$

(GTKWifi:11414): Bonobo-WARNING **: Never got frame, control died - abnormal exit condition


```
i uninstall it using synaptic and the completly and absolutly remove any trace of the son-of-a-gun option (or whatever it's called)
now when i try ifup or ifdown to connect to my wireless, internet
i get this error
```

laserwolf@violet:~$ sudo ifdown wlan0
password:
There is already a pid file /var/run/dhclient.wlan0.pid with pid 7595
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:44:ed:eb
Sending on   LPF/wlan0/00:0f:b5:44:ed:eb
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.254 port 67


laserwolf@violet:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:44:ed:eb
Sending on   LPF/wlan0/00:0f:b5:44:ed:eb
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.254
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.254
bound to 192.168.1.65 -- renewal in 33569 seconds.

```

oddly enough, when i started my computer up this morning, it told me new updates were available
and it had the correct time (my motherboard battery is out of juice? so i have to reset bios settings every time i log in, including system time... most of the time i leave the time alone and worry about the important stuff)

i have a DHCP connection with my pci 802.11b wireless card to my 802.11b/g router
AMD xp 2200+
512mb RAM
1 80gb HD w/ windows XP on it
and a 200GB hd w/ linux and 4 storage partitions
i've also got a wifi antennae that ussually gives me a "good" connectivity in windows

---

### Post by ren wins on 2005-11-29
i would really like some help with this
b/c reinstalling ubuntu for the 3rd time to fix a wifi problem seems like a lot of overkill

---

### Post by ren wins on 2005-11-30
so these are the files that ifup and ifdown seem to have problems with

dhclient.wlan0.leases:
```
lease {
  interface "wlan0";
  fixed-address 192.168.1.65;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 86400;
  option routers 192.168.1.254;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.254;
  option domain-name-servers 192.168.1.254;
  option dhcp-renewal-time 43200;
  option dhcp-rebinding-time 75600;
  option domain-name "gateway.2wire.net";
  renew 2 2005/11/29 21:34:10;
  rebind 2 2005/11/29 21:34:10;
  expire 2 2005/11/29 21:34:10;
}
lease {
  interface "wlan0";
  fixed-address 192.168.1.65;
  option subnet-mask 255.255.255.0;
  option dhcp-lease-time 86400;
  option routers 192.168.1.254;
  option dhcp-message-type 5;
  option dhcp-server-identifier 192.168.1.254;
  option domain-name-servers 192.168.1.254;
  option dhcp-renewal-time 43200;
  option dhcp-rebinding-time 75600;
  option domain-name "gateway.2wire.net";
  renew 3 2005/11/30 04:52:01;
  rebind 3 2005/11/30 04:52:01;
  expire 3 2005/11/30 04:52:01;
}

```

and dhclient.pid
```

10671

```

---

