---
title: "Login delay without network connection"
date: 2005-01-18
forum: General Help
---

### Post by metallikop on 2005-01-18
I'm sure this is something very basic that I'm missing.  Without a network connection it takes quite a while to get a login prompt and issuing any sudo commands.  Also, at bootup syslog takes a while to start up, I'm guessing for the same reason

I'm assuming it's DNS related problem.  I have an extensive hosts file (yuck) but I do have localhost as the first entry.

```
alake@mesaana:~ $ head -1 /etc/hosts
127.0.0.1 mesaana localhost.localdomain localhost
alake@mesaana:~ $ wc -l /etc/hosts
70 /etc/hosts
```

Ideas?

---

### Post by randy on 2005-01-18
It might be because you have your network device set to try to get an ip when your booting.

---

### Post by mendicant on 2005-01-19
It could also be the ntp syncing, which can take a bit of time to detect that there's no interface.  You can always edit /etc/default/ntpdate so this never happens (by changing NTPSERVERS to be empty, or you can add a little bit of logic to the start of /etc/init.d/ntpdate to check if it can ping the server ping -c 3 $NTPSERVERS, assuming you only use one server.  If it fails, exit early.

---

