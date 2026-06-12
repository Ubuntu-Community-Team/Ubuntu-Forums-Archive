---
title: "What's the equivalent of ipconfig/all in Ubuntu?"
date: 2009-04-05
forum: General Help
---

### Post by alcatraz678 on 2009-04-05
Hi,

I want to port forward my uTorrent in Ubuntu but I couldn't because I don't know my local ip address. How can I can that here?

---

### Post by d3ngar on 2009-04-05
Try:

```
ifconfig
```

This command is very useful when you want to check on your wireless:

```
iwconfig
```

- Chris

---

### Post by Yashiro on 2009-04-05
> 
/sbin/ifconfig | awk /'inet addr/ {print $2}'
/sbin/ifconfig | awk /'Bcast/ {print $3}'
/sbin/ifconfig | awk /'HWaddr/ {print $4,$5}'
wget [http://checkip.dyndns.org/](http://checkip.dyndns.org/) -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1


Top one is internal IP.
Bottom one is external IP.

Put it in a script or something. :)

---

### Post by alcatraz678 on 2009-04-06
Thank you thank you very much for the help

---

