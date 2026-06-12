---
title: "DHCP3 dhclient.conf: expecting a statement"
date: 2009-05-18
forum: General Help
---

### Post by schuey on 2009-05-18
Hi all, very new to Linux.....never thought I would uninstall my windows server and install ubuntu.
 
Im setting up the dhcp on my server and have installed dhcp3. I have found the configuration file in /etc/dhcp3/dhclient.conf .....I have then gone through and added the following code:
 
```

send host-name "<webServer>";
authoritative;
subnet 192.168.97.0 mask 255.255.255.0
{
range 192.168.97.2 192.168.97.10;
dns-update-style none;
option domain-name "harding.local";
option domain-name-servers 192.231.203.132, 192.231.203.3;
option routers 192.168.97.1;
default-lease-time 42300;
max-lease-time 84600;
}   

```
 
I then save this configuration and run dhclient but I get the following errors:
line1: expecting a statement
line3: semicolon expected
 
Is there anything I have done wrong in the configuration file to get these two errors. Any help would be great
 
Thanks

---

