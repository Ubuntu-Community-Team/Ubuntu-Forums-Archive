---
title: "One reason why Linux is not for everyone! Iptables!"
date: 2006-01-06
forum: Desktop Environments
---

### Post by theFallen on 2006-01-06
Hello,

so I'm new to Linux and I used Ubuntu 'til wanted something new. I used there Firestarter after changing to Kubuntu I had naught and tried to understand Iptables...

Okay, for now I have installed Firestarter again.

Can someone tell mme what Chains these are:

Chain INBOUND (1 references)                                                                                                                                   
Chain INPUT (policy DROP)     
Chain FORWARD (policy DROP)
Chain LOG_FILTER (5 references)
Chain LSI (2 references)
Chain LSO (0 references)
Chain OUTBOUND (1 references)
Chain OUTPUT (policy DROP)

Okay, I think INBOUND OUTBOUND is clear but the rest...
And where is this damn file?

---

### Post by Omnios on 2006-01-06
Google search "Firestarter Linux ip tables chains guide"

chains are a bit down the page
[http://www.tipmonkies.com/2005/07/08/writing-linux-firewall-rules-w-iptables]("http://www.tipmonkies.com/2005/07/08/writing-linux-firewall-rules-w-iptables")

---

### Post by scylax on 2006-01-08
You don't need all of those chains. The 5 chains that you do need are :
From the FILTER table :

INPUT : concerning packets addressed to the firewall *itself*
OUTPUT : the same, for packets coming out of the firewall *itself*
FORWARD : for packets that will pass through the firewall, but are addressed 
to/coming from a different subnet (ie. internet->LAN, LAN->internet, internet->DMZ...)

From the nat table :

PREROUTING : allows you to change the destination address, usually used in port forwarding
POSTROUTING : allows you to change the source address, used to do network address translation (NAT)

Quick & easy example: a firewall with two network cards eth0 and eth1. eth0 is connected to a LAN, eth1 is connected to the internet. The firewall and the LAN will be able to browse the internet (http, https, dns) and nothing more ;) :

#!/bin/sh
# Iptables example script
echo Starting iptables...
LAN_IP=192.168.0.0/24
# Flush
iptables -Z
iptables -X
iptables -F
iptables -t nat -F
# Default policy: everything is forbidden
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# This firewall is a router
echo 1 > /proc/sys/net/ipv4/ip_forward
# and a NAT router at that
iptables -t nat -A POSTROUTING -s $LAN_IP -o eth1 -j MASQUERADE
# The firewall will be able to browse the Web
iptables -A OUTPUT -o eth1 -p tcp --dport 80 -j ACCEPT
iptables -A OUTPUT -o eth1 -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth1 -p tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -o eth1 -p udp --dport 53 -j ACCEPT
iptables -A INPUT -i eth1 -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Our LAN will also browse the Web

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 80 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A FORWARD -i eth0 -o eth1 -p tcp --dport 443 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -p tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT

iptables -A FORWARD -i eth0 -o eth1 -p udp --dport 53 -j ACCEPT
iptables -A FORWARD -i eth1 -o eth0 -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT

# end

save as iptables_script, chmod +x iptables_script, and copy it to /etc/network/if-pre-up.d/. That way it'll be executed every time networking is initialized.

---

### Post by theFallen on 2006-01-09
Thanks to you all,

slowly I will get it. But again, its nothing a simple user can do. The mass is stupid. 

I changed the script a bit and have some more questions. I have a router and my PC is connected to it. So there is no eth1.

#!/bin/sh
# Iptables example script
echo Starting iptables...

#THIS LINE DOES WHAT? IS IT A RANGE OF IP-ADDRESSES?
#LAN_IP=192.168.0.0/24

# Flush
iptables -Z
iptables -X
iptables -F
iptables -t nat -F

# Default policy: everything is forbidden
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# This firewall is a router

#WHY THIS LINE?
echo 1 > /proc/sys/net/ipv4/ip_forward

# and a NAT router at that
#I DON'T HAVE eth1 DO I SIMPLY CHANGE IT TO eth0? WHAT DOES POSTROUTING
#iptables -t nat -A POSTROUTING -s $LAN_IP -o eth1 -j MASQUERADE

# The firewall will be able to browse the Web
#FTP
	iptables -A INPUT -i eth0 -p tcp --sport 20-21 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 20-21 -j ACCEPT
#HTTP
	iptables -A INPUT -i eth0 -p tcp --sport 80 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 80 -j ACCEPT
#HTTPS
	iptables -A INPUT -i eth0 -p tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 443 -j ACCEPT
#POP3
	iptables -A INPUT -i eth0 -p tcp --sport 443 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 443 -j ACCEPT
#SMTP
	iptables -A INPUT -i eth0 -p tcp --sport 25 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 25 -j ACCEPT
#DNS
	iptables -A INPUT -i eth0 -p udp --sport 53 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p udp --dport 53 -j ACCEPT
#Azureus
	iptables -A INPUT -i eth0 -p tcp --sport 65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p tcp --dport 65535 -j ACCEPT
	iptables -A INPUT -i eth0 -p udp --sport 65535 -m state --state ESTABLISHED,RELATED -j ACCEPT
	iptables -A OUTPUT -o eth0 -p udp --dport 65535 -j ACCEPT

# end


What about UDP, which Protocol is using it? If I hadn't allready enough on my plate I would spend some time reading corresponding stuff, but.....

---

### Post by Divan Santana on 2006-01-09
Hey! iptables and firewalling for linux is fine!!

Iptables is complex no doubt but you DONT have to understand it to setup complex firewalling.

I would strongly recommend guarddog(firewalling) and guidedog(for masq).
Guarddog can setup a really excellent firewall so simply on KDE/Linux!

No rule editing.

If you need more complex stuff learn ZONES in guarddog but clicking on help.

I have many complex firewalls setup with guarddog. Wish new version would come out soon :)

---

### Post by nocturn on 2006-01-09
Wow, just because you have the option to actually look at your firewall tables does not make Linux unsuiteable for 'everyone'.

You do not need to use iptables, you can use the numerous frontends that are out there and a firewall is not a requirement on Ubuntu as it does not have any open ports (default install).

---

### Post by theFallen on 2006-01-09
Its not only the iptables I'm talking about, what it makes hard for "ungifted" users to use linux. I studie informatics, so I think I am quite capable handling a computer. But I've seen people who are totally overcharged with the console, mounting drives, installing software.
I'd say WinXP is a bit more intuitive and for sure handles (to my dismay) a lot more hardware than linux. The why is unimportant here.
And for a user who wants to get some work done has definitly no time to read some manuals, post etc.
It just has to work properly after making some clicks. Thats why GUIs were invented.

But back to topic. I tried out guarddog and I didn't like it. It didn't even change the current iptable. At least when I typed 
$iptables -L
I could see no changes.

---

### Post by Velvet Elvis on 2006-01-09
IIRC, guarddog uses IP chains rather than IP tables.

IP chains was the default firewalling method in 2.4 series kernels and has been depreciated in 2.6 but should still work fine.

Right now I'm using KMyFirewall with mostly default settings and it seems to be working OK for a basic desktop firewall.

If you prefer the more hands on approach try using webmin to set up shorewall.  I find it more intuitive than setting up IP tables by hand.

Webmin is an awesome configuration tool for people who have some understanding of how stuff works under the hood but still prefer a GUI.  That it allows for easy remote administration is an added bonus.

IMHO, the problem with linux isn't that there are too many tools out there which do pretty much the same thing but rather that there is almost no way to figure out which one is best for what you're trying to do.

---

### Post by calt129 on 2006-01-20
*I'm not sure if you're familiart with iptables concepts, but in case there are other people reading this thread...*

You should definitely read the [tutorials on netfilter.org]("http://www.netfilter.org/documentation/index.html#documentation-howto"), they're pretty condensed yet easy to understand:

[networking-concepts-HOWTO]("http://www.netfilter.org/documentation/HOWTO/networking-concepts-HOWTO.html")
[packet-filtering-HOWTO]("http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html")
[NAT-HOWTO]("http://www.netfilter.org/documentation/HOWTO/NAT-HOWTO.html")

Netfilter is a framework, to which iptables also belongs. Iptables is the so-called userland interface for the iptables functionality in kernel. Linux has the firewalling functionality embedded in kernel and the command *iptables* is the interface to control the parameters for this kernel module. **One of the most important schemes** IMO is on the following page, it gives you an overview of what chains are and how they are traversed:

[How Packets Traverse The Filters]("http://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO-6.html")

---

