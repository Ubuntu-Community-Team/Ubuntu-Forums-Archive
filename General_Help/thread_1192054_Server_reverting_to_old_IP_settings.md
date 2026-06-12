---
title: "Server reverting to old IP settings"
date: 2009-06-19
forum: General Help
---

### Post by jasch on 2009-06-19
I installed Ubuntu 9 yesterday, the server by default was on DHCP mode, so I edited /etc/network/interfaces and made the appropiate changes from dynamic to a static ip.

I do a sudo /etc/init.d/networking restart

And the server changes IP, and everything works great.

But after a couple of hours, somehow it reverts back to DHCP (old IP address).

I have to ssh to the old ip, do another sudo /etc/init.d/networking restart and everything starts working again.

It's happened 3 times in the last 24 hours, and I cannot restart this server at this point.

Any ideas what the problem is?

Thanks in advance.

---

### Post by pytheas22 on 2009-06-19
That's strange.  What exactly does your /etc/init.d/interfaces file look like (obfuscate the IP address before posting here)?

And does dmesg say anything that would offer a clue?

---

### Post by jasch on 2009-06-19
You mean /etc/network/interfaces right?

No need to obsfuscate, it's a private ip:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet static
address 192.168.1.203
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

I don't see anything in dmesg that would indicate any problems.

Will check again next time it happens (hard to figure out, since there are no date stamps)

---

### Post by pytheas22 on 2009-06-19
The file looks fine to me.  You could try commenting out the network and broadcast lines, as they shouldn't be necessary in most cases and could be causing the problem somehow.

> 
Will check again next time it happens (hard to figure out, since there are no date stamps) 

Try looking at /var/log/syslog instead.  It has timestamps.

---

### Post by dcstar on 2009-06-20
> **jasch said:**
> I installed Ubuntu 9 yesterday, the server by default was on DHCP mode, so I edited /etc/network/interfaces and made the appropiate changes from dynamic to a static ip.
.........

Did you install using the Ubuntu **Desktop** or **Server** CD?

---

