---
title: "ubuntu networking does not save DNS"
date: 2006-06-12
forum: Desktop Environments
---

### Post by NasosUb on 2006-06-12
i configure with the use of Gnome Network-admin the DNS addresses but each time i restart the computer it seems they disappear and cannot use the internet. I have tried to insert them in the /etc/dhcp3/dhcp.conf and configure /etc/network/interfaces but nothing has changed. 

Please help me !!! :D

---

### Post by cyrus7580 on 2006-06-12
I've been having the same issue. I change the DNS servers in the gnome-gui config or change them manually in /etc/resolv.conf, but they always change back. It's as if some cron job keeps resetting them to use my ISP's servers (which suck).

I'm a decade-long redhat user and just now switching to Ubuntu, these kinds of "which script does what" issues are killing me.

---

### Post by cyrus7580 on 2006-06-12
This may help. I haven't tried it yet, but it looks promising.

[https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28staticdns%29](https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28staticdns%29)

---

### Post by tobiaspb on 2006-06-12
Hi.

Have you tried to install resolvconf?

```
sudo apt-get install resolvconf
```

Maybe that will help with the discovery of the DNS servers. If not, adding the lines to the /etc/network/interfaces as described should help.

---

### Post by NasosUb on 2006-06-13
thank you cyrus7580 the link was helpful and helped me to fix the problem. now the dns is saved.

---

