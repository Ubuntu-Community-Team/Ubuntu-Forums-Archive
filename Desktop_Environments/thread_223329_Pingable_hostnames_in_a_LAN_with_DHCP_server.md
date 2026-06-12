---
title: "Pingable hostnames in a LAN with DHCP server"
date: 2006-07-26
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-26
Hi,

I'm actually installing Ubuntu 6.06 in a small LAN, and I wonder how machines could become pingable by their hostnames (e. g. not only by their IPs). Here's my setup.

**1. On the server:**

```

# /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
```

```
# /etc/hosts

127.0.0.1       localhost.localdomain localhost
127.0.0.1       bertha.kikinovak.net bertha

192.168.1.1     bertha.kikinovak.net bertha
```

```
# dhcpd.conf

ddns-update-style none;
default-lease-time 259200;
max-lease-time 518400;

subnet 192.168.1.0 netmask 255.255.255.0
{
        option routers 192.168.1.1;
        option broadcast-address 192.168.1.255;
        option domain-name-servers 213.36.80.1;
        option domain-name "kikinovak.net";
        range 192.168.1.2 192.168.1.252;
}

host nordine
{
        hardware ethernet 00:0b:cd:7a:3d:3a;
        fixed-address 192.168.1.4;
}
```

**2. On the clients side:**

```
# /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

```

# /etc/hosts
127.0.0.1       localhost.localdomain localhost
127.0.0.1       nordine.kikinovak.net nordine
```

Now here's what looks like the first redundancy to me. The hostname above ("nordine") is already somewhat defined on the server's dhcpd.conf. I tried to leave it out in the hosts file on the client side, but the system complained about having no hostname.

I'll try to describe my ignorance of the thing as accurately as possible, but I guess I'm looking for a DHCP setup that not only distributes IP addresses, but also hostnames. Sort of like distributed /etc/hosts files. The main interest of DHCP being to me (correct me if I'm wrong) *not* to have to manually maintain a bunch of /etc/hosts files on the clients (or else, I would have configured everything statically in the first place).

Any suggestions for that?

---

### Post by cilynx on 2006-07-26
Personally, I use dnsmasq on my gateway.

```

root@seriph:~# cat /etc/dnsmasq.conf 
# filter what we send upstream
domain-needed
bogus-priv
filterwin2k
localise-queries

# allow /etc/hosts and dhcp lookups via *.lan
local=/lan/
domain="lan"
expand-hosts

# enable dhcp (start,end,netmask,leasetime)
dhcp-authoritative
#dhcp-range=192.168.1.100,192.168.1.250,255.255.255.0,12h
dhcp-leasefile=/tmp/dhcp.leases

# use /etc/ethers for static hosts; same format as --dhcp-host
# <hwaddr> <ipaddr>
read-ethers

# other useful options:
# default route(s): dhcp-option=3,192.168.1.1,192.168.1.2
#    dns server(s): dhcp-option=6,192.168.1.1,192.168.1.2
root@seriph:~# 

```

... and dhclient on my clients...

```

rcw@angus:~$ cat /etc/dhcp3/dhclient.conf
send host-name "angus";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
rcw@angus:~$ 

```

That setup Just Works for me.  Just for the record, my gateway is a Linksys WRT54GS running OpenWRT White Russian rc5 and all of my clients at the moment are Ubuntu Dapper or Edgy.  I have run the same setup using both Ubuntu and Debian machines as gateway and Debian, SuSe, and Win* machines as client.

---

### Post by kikinovak on 2006-07-26
Thanks very much for that detailed answer!

---

