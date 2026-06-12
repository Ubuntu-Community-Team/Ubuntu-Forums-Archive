---
title: "Need help configuring /etc/hosts file (Server)"
date: 2009-03-07
forum: General Help
---

### Post by garrett1415 on 2009-03-07
I'm in the middle of configuring a Ubuntu 8.04 LTS server. I'm on the step where I have to configure the /etc/hosts file, and frankly, I'm stuck.

Heres what I'm looking at:

127.0.0.1 localhost
127.0.1.1 server1.Belkin server1
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I need to know what I need to fill in here. The guide I'm using says it should look something like this:

127.0.0.1 localhost.localdomain localhost
192.168.0.100 server1.example.com server1
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I'm not sure what to fill in for the first and second lines.

Thanks

---

### Post by cariboo on 2009-03-07
Substitute your server name for:

> server1.example.com server1

if you use the name in the first example, it would be:

```
192.168.0.100  server1.Belkin  server1
```

Jim

---

### Post by dcstar on 2009-03-07
> **garrett1415 said:**
> I'm in the middle of configuring a Ubuntu 8.04 LTS server. I'm on the step where I have to configure the /etc/hosts file, and frankly, I'm stuck.
........
I need to know what I need to fill in here. The guide I'm using says it should look something like this:

127.0.0.1 localhost.localdomain localhost
192.168.0.100 server1.example.com server1
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I'm not sure what to fill in for the first and second lines.

Thanks

Just keep in mind that this table is essentially a way of making aliases for the values:

127.0.0.1 is an alias for the DNS name localhost.localdomain OR localhost, localhost.localdomain OR localhost is an alias that returns 127.0.0.1 as the resolved IP address.

You do the same thing with other IP addresses that you put in the file (as many as you like - internal to your system as well as external ones).

Don't forget to also set your /etc/hostname file to have a name that matches an entry in the /etc/hosts file.

---

