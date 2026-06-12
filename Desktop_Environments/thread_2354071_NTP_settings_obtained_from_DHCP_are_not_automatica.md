---
title: "NTP settings obtained from DHCP are not automatically reflected."
date: 2017-02-27
forum: Desktop Environments
---

### Post by fude-kun on 2017-02-27
In Ubuntu 14.04 LTS.

I am using a DHCP server that includes NTP destination.

"/var/lib/NetworkManager/dhclient-hogehoge-wlan0.lease" certainly confirms that it is receiving the address of the NTP server.

```

lease {
interface "wlan0";
fixed-address 192.168.10.183;
option subnet-mask 255.255.255.0;
option dhcp-lease-time 7776000;
option routers 192.168.10.1;
option dhcp-message-type 5;
option dhcp-server-identifier 192.168.10.1;
option domain-name-servers 192.168.10.1,8.8.8.8;
option dhcp-renewal-time 3888000;
option dhcp-rebinding-time 6804000;
option broadcast-address 192.168.10.255;
option ntp-servers 192.168.10.1,192.168.10.2;
option host-name "hogehoge";
renew 5 2017/04/07 05:09:59;
rebind 3 2017/05/17 18:55:49;
expire 1 2017/05/29 00:55:49;
}

```


"Request ntp-servers" is set in "/var/lib/NetworkManager/dhclient-wlan0.conf".
```

request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, domain-search, host-name,
dhcp6.name-servers, dhcp6.domain-search,
netbios-name-servers, netbios-scope, interface-mtu,
rfc3442-classless-static-routes, ntp-servers,
dhcp6.fqdn, dhcp6.sntp-servers;

```

However, connecting to this DHCP server does not overwrite the NTP settings, I am in trouble.

The "sudo dhclient wlan0" command was used.
With this command, when DHCP reassignment is executed, it was confirmed that the value of NTP server is overwritten !!!!!

I can not understand this phenomenon.

For connection to WiFi, it was set using "Network Manager GUI". 
Does this have something to do with the phenomenon that is happening to me?

Please help me.

---

