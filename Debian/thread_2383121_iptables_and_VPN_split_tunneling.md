---
title: "iptables and VPN split tunneling"
date: 2018-01-21
forum: Debian
---

### Post by ractive74 on 2018-01-21
So I'm setting up a VPN split-tunnel for my box (raspberry pi 3/Debian stretch) so network traffic for user 'vpn' goes through interface 'tun0' and traffic for other users go through 'eth0'. I've followed this guide: [https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/](https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/) and had no problems getting it all working fine. User 'vpn' gets the openvpn (tun0) IP and others get the regular IP. I'm running aria2c (a torrenting client) as user 'vpn'. The problem is that aria2c has a RPC deamon that I can connect to to control, view, add, pause, etc the downloads that runs on port 6800 by default, and I can't connect to it with this setup from my lan (I think because I'm trying to connect to 192.168.1.43 and the RPC server is running on the VPN ip) So...all that said I think I need a way to forward port 6800 from eth0 to tun0, but I have no clue how to do that... I'm not familiar with iptables as I have been very lazy and just used ufw to configure firewalls.

here are my current iptables rules (copied direct from the guide)
```

#! /bin/bash
# Niftiest Software – www.niftiestsoftware.com
# Modified version by HTPC Guides – www.htpcguides.com

export INTERFACE="tun0"
export VPNUSER="vpn"
export LOCALIP="[COLOR=#3366ff]192.168.1.43[/COLOR]"
export NETIF="[COLOR=#ff0000]eth0[/COLOR]"

# flushes all the iptables rules, if you have other rules to use then add them into the script
iptables -F -t nat
iptables -F -t mangle
iptables -F -t filter

# mark packets from $VPNUSER
iptables -t mangle -A OUTPUT -j CONNMARK --restore-mark
iptables -t mangle -A OUTPUT ! --dest $LOCALIP -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT --dest $LOCALIP -p udp --dport 53 -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT --dest $LOCALIP -p tcp --dport 53 -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT ! --src $LOCALIP -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT -j CONNMARK --save-mark

# allow responses
iptables -A INPUT -i $INTERFACE -m conntrack --ctstate ESTABLISHED -j ACCEPT

# block everything incoming on $INTERFACE to prevent accidental exposing of ports
iptables -A INPUT -i $INTERFACE -j REJECT

# let $VPNUSER access lo and $INTERFACE
iptables -A OUTPUT -o lo -m owner --uid-owner $VPNUSER -j ACCEPT
iptables -A OUTPUT -o $INTERFACE -m owner --uid-owner $VPNUSER -j ACCEPT

# all packets on $INTERFACE needs to be masqueraded
iptables -t nat -A POSTROUTING -o $INTERFACE -j MASQUERADE

# reject connections from predator IP going over $NETIF
iptables -A OUTPUT ! --src $LOCALIP -o $NETIF -j REJECT

# Start routing script
/etc/openvpn/routing.sh

exit 0
```[URL="https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/"]
[/URL]
here is the routing stuff:
```
#! /bin/bash
# Niftiest Software – www.niftiestsoftware.com
# Modified version by HTPC Guides – www.htpcguides.com

VPNIF="tun0"
VPNUSER="vpn"
GATEWAYIP=$(ifconfig $VPNIF | egrep -o '([0-9]{1,3}\.){3}[0-9]{1,3}' | egrep -v '255|(127\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3})' | tail -n1)
if [[ `ip rule list | grep -c 0x1` == 0 ]]; then
ip rule add from all fwmark 0x1 lookup $VPNUSER
fi
ip route replace default via $GATEWAYIP table $VPNUSER
ip route append default via 127.0.0.1 dev lo table $VPNUSER
ip route flush cache

# run update-resolv-conf script to set VPN DNS
/etc/openvpn/update-resolv-conf

exit 0
```

and the routing table:
```
#
# reserved values
#
255     local
254     main
253     default
0       unspec
#
# local
#
#1      inr.ruhep
[COLOR=#ff0000]200     vpn[/COLOR]
```

and here is the output of iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
f2b-recidive  tcp  --  anywhere             anywhere            
f2b-sshd   tcp  --  anywhere             anywhere             multiport dports 2222
ACCEPT     all  --  anywhere             anywhere             ctstate ESTABLISHED
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             owner UID match vpn
ACCEPT     all  --  anywhere             anywhere             owner UID match vpn
REJECT     all  -- !192.168.1.43         anywhere             reject-with icmp-port-unreachable

Chain f2b-recidive (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain f2b-sshd (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain monitorix_IN_0 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_1 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_2 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_3 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_4 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_5 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_6 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_7 (0 references)
target     prot opt source               destination         

Chain monitorix_IN_8 (0 references)
target     prot opt source               destination  
```

So any help I can get would be very much appreciated. Thank you.

---

### Post by howefield on 2018-01-21
Thread moved to the "*Debian*" forum.

---

