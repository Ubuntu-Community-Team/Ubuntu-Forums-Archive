---
title: "Problems with ip forwarding"
date: 2005-06-19
forum: Desktop Environments
---

### Post by blixel on 2005-06-19
Sorry - I'm new here.  I posted this question to the wrong area but I don't see anyway to move it now that it's posted.

I'm trying to use my laptop as a quick and dirty router for another machine I have.

My laptop has a wireless connection and a 10/100Mb Ethernet port.

I want to plug in my other machine to my laptop's wired Ethernet port (via a cross over network cable) and be able to access the Internet from that other machine.  This seems like it would have been a simple thing to do but I can't make it work.

I statically assigned 192.168.100.1 to my laptop's Ethernet port.

I statically assigned 192.168.100.2 to my other machine and set 192.168.100.1 as the default gateway.

Those two machines are able to ping each other's 192.168.100.x address.  (So that tells me the cross over cable is working at least.)

I then ran:

```
echo "1" > /proc/sys/net/ipv4/ip_forward
```

on my laptop to enable ip forwarding.  I also checked the iptables to make sure there wasn't any kind of port blocking.

```
iptables -L
```

The iptables command showed that everything was open.

At that point, I expected to be able to ping the local router from the 192.168.100.2 machine.  I had not yet setup my /etc/resolv.conf on the 192.168.100.2 machine so I knew I wouldn't be able to ping host names yet.

This is where I'm stuck.

From the 192.168.100.2 machine I can ping the IP address of the laptop's **wired** port, and I can ping the IP address of the laptop's **wireless** card.  However, I can not ping any other machines on the network, nor can I ping the local router.

What am I missing?

---

### Post by poofyhairguy on 2005-06-19
[QUOTE=blixel]Sorry - I'm new here.  I posted this question to the wrong area but I don't see anyway to move it now that it's posted.[/QUOTE]

I can do it.

---

### Post by sksbir on 2005-06-19
crossposting is not a good idea.. next is to read here : [http://ubuntuforums.org/showthread.php?t=42816](http://ubuntuforums.org/showthread.php?t=42816)

---

