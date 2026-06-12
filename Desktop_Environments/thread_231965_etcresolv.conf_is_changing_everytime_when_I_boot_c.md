---
title: "/etc/resolv.conf is changing everytime when I boot computer"
date: 2006-08-08
forum: Desktop Environments
---

### Post by 5hark on 2006-08-08
I have internet connection via ADSL (Dlink DSL-500T modem), modem is configured as bridge, also there is DHCP server running on it. Modem connected to computer with ethernet card (eth0 192.168.1.2). I run pppoeconf and configured PPPoE connection, here is config:

```
**/etc/network/interfaces**
auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0


auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

**/etc/ppp/peers/dsl-provider**
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "username"

```

During startup pppoe connection is launching, but it seems that dns servers are not replaced (modem`s dhcp server gives his own ip address 192.168.1.1). If I launch $ sudo poff dsl-provider && pon dsl-provider, /etc/resolv.conf updates with correct dns servers from provider`s dhcp.

I can`t turn off dhcp server on my modem, can I change something else to get correct dns servers from provider?

Here is bootchart ~300Kb
[[IMG]http://img79.imageshack.us/img79/5422/dapper200608081vw1.th.png[/IMG]](http://img79.imageshack.us/my.php?image=dapper200608081vw1.png)

---

### Post by wieman01 on 2006-08-08
Actually the router's address should also be your DNS server... Nonetheless, if you want to prevent the system from changing the file, then simply make it read-only after you have edited it:

> sudo chmod -w /etc/resolv.conf

The system won't be able to change it after this has been done.

---

### Post by 5hark on 2006-08-08
My router has only one ip address now - 192.168.1.1 because it configured as bridge, so it can`t serve dns requests. Correct /etc/resolv.conf is

```
nameserver 212.188.4.10
nameserver 195.34.32.116
```

This file must be writable because ppp need to change it when provider send me correct dns server addresses. Maybe there is some option that help ppp change /etc/resolv.conf?

---

### Post by h00s on 2006-08-08
Here's another solution.

Put your dsl modem in router mode (On D-link support pages says that it supports router mode). Then you dont need to set up pppoe on computer, just configure computer to use modem-router as gateway.

---

### Post by wieman01 on 2006-08-08
> **5hark said:**
> My router has only one ip address now - 192.168.1.1 because it configured as bridge, so it can`t serve dns requests. Correct /etc/resolv.conf is

```
nameserver 212.188.4.10
nameserver 195.34.32.116
```

This file must be writable because ppp need to change it when provider send me correct dns server addresses. Maybe there is some option that help ppp change /etc/resolv.conf?

DNS servers don't change... So once you have received the correct DNS IP addresses you could lock the file. That's it.

---

### Post by Buffalo Soldier on 2006-08-08
> **5hark said:**
> My router has only one ip address now - 192.168.1.1 because it configured as bridge, so it can`t serve dns requests. Correct /etc/resolv.conf is```
nameserver 212.188.4.10
nameserver 195.34.32.116
```This file must be writable because ppp need to change it when provider send me correct dns server addresses. Maybe there is some option that help ppp change /etc/resolv.conf?

I think what you want to do here is to tell the DHCP Client to use a set of default DNS addresses. Go to the terminal/command line:
```
sudo gedit /etc/dhcp3/dhclient.conf
```Look for this line:
```
#prepend domain-name-servers 127.0.0.1;
```and change it to:
```
prepend domain-name-servers 212.188.4.10, 195.34.32.116;
```
Do not forget to delete/remove the **[color=red]#[/color]** character at the start of the line.

What is supposed to happen now is everytime you reboot or your DHCP Client refresh, it will add those two addresses to your resolve.cont file.

Reference: [http://ubuntuforums.org/showpost.php?p=1322888&postcount=41](http://ubuntuforums.org/showpost.php?p=1322888&postcount=41)

---

