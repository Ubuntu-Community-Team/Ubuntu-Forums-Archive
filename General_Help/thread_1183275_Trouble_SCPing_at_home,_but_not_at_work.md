---
title: "Trouble SCPing at home, but not at work"
date: 2009-06-09
forum: General Help
---

### Post by BrainInVat on 2009-06-09
I can scp files from a remote host to my laptop at work, but when I take my laptop home and try to scp files from the same remote host to my laptop it says

connect to host ********* port 22: Connection refused
lost connection

I have already installed openssh-server.  Thanks for your help in advance.

---

### Post by dmizer on 2009-06-09
You cannot use your extermal domain to connect to your server while you're on your LAN. You can fix this one of two ways:

1) Use your server's IP address instead.
2) Add your servers extermal domain to your /etc/hosts file.

For example: If my external domain is [noparse]me.dyndns.com[/noparse], and my server's LAN IP address is 192.168.1.101, then my /etc/hosts will look like this:
```
127.0.0.1       localhost
127.0.1.1       xubuntu-ibex
[COLOR="Red"]192.168.1.101   me.dyndns.com[/COLOR]
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Then I can scp/ssh via ssh [noparse]me@me.dyndns.com[/noparse] while in my LAN.

---

