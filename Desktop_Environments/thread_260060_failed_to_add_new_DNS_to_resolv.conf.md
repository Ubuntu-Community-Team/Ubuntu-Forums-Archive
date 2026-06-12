---
title: "failed to add new DNS to resolv.conf"
date: 2006-09-18
forum: Desktop Environments
---

### Post by zhaiduo on 2006-09-18
hi, I add a new dns to /etc/resolv.conf with root sudo. but it disappeared when I restart ubuntu, what's wrong with it?:confused:

---

### Post by kidders on 2006-09-18
You may be acquiring your network address via DHCP, which naturally rewrites resolv.conf according to the information received from the server. You can however suppress this behaviour if you really want to ...

Take a peek at /etc/dhcp3/dhclient.conf. I *think* that's where you need to look :-)

---

### Post by zhaiduo on 2006-09-18
Thanks for your help, really appreciate it:lol: :-\" =D> =D>

---

### Post by kidders on 2006-09-18
Sounds like I found your problem :-) Excellent :biggrin:

---

