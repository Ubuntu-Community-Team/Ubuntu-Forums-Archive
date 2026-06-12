---
title: "iproute script messes up samba and cifs, how can I fix this?"
date: 2009-01-21
forum: General Help
---

### Post by Thasp on 2009-01-21
Hi,

I wanted to be able to have separate NICs with separate IPs connecting to separate gateways on a machine so I could put an ftpd on each one. I tried binding an ftpd to each, and running separate instances of the ftpd. I tried virtual hosts. 

NOTHING worked. I could either use one ftpd or the other. I could either connect via ssh on one IP or the other. the second I turned one NIC off stuff would work again. I messed with basic iproute commands, andnothng worked until I got this script to run, which allowed me to use each NIC independant of the other.

```
#!/bin/sh
#ip route flush all

ip route del default dev eth1
ip route del default dev eth0

ip route del table 1
ip route add table 1 to default via 10.10.10.1 dev eth1

ip route del table 2
ip route add table 2 to default via 192.168.1.1 dev eth0

ip rule add from 10.10.10.2 table 1
ip rule add from 192.168.1.248 table 2

ip route add default via 10.10.10.1 dev eth1

```

But now, samba client doesn't work. cifs mounting doesn't work either. It can't connect. Both work fine before I run the script. 

BEFORE I ran that script, I could connect via ssh, or to the ftpd running on the machine using a LOCAL IP - 10.10.10.2. AFTER, I have to use the external IP, or I cannot connect. I know that has something to do with it, but I do not have the advanced linux routing knowledge to redo the script or come up with a solution.

Thanks.

---

### Post by Thasp on 2009-01-21
made the script more machine specific generic so it's easier to read.

---

### Post by Thasp on 2009-01-22
nobody loves me :(:cry::cry:

---

