---
title: "How can I manually enter the Gateway IP?"
date: 2006-03-28
forum: Desktop Environments
---

### Post by joejac on 2006-03-28
For some strange reason today I am not able to connect my Kubuntu desktop to internet, it was working before. I use a Linux machine with Shorewall as a firewall-router, its IP is 192.168.0.1 I was able to connect last time, but suddenly Kubuntu client have lost the gateway IP.

I try to enter it manually via KDE but it do not allow me to update it. It never updates. I am linux novice, can some body tell me how do I enter my gateway IP number in the correct configuration file?

Please provide with all the path and file name, so I can enter this information manually via the console.

This is a home network and my other 2 Windows PC's are able to connect with no problem at all.

Thanks a lot
joejac

---

### Post by rattking on 2006-03-28
Hi
its in /etc/network/interfaces

iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        gateway 192.168.0.1

---

### Post by joejac on 2006-03-28
Thanks! rattking, how fast help. It worked. These forums and the community are really great, very nice people.
Regards
joejac

---

