---
title: "can't get swat to work"
date: 2006-01-15
forum: General Help
---

### Post by pk_volt on 2006-01-15
so I have both samba and swat installed

this is what I have in my inetd.conf

netbios-ssn     stream  tcp     nowait          root    /usr/sbin/tcpd/usr/sbin/smbd
swat            stream  tcp     nowait.400      root    /usr/sbin/swat swat

i also have port 901 opened in my router settings

also have this in my hosts.allow
swat: 192.168.0.100

---

### Post by Mr_Grieves on 2006-01-15
Have you verified that swat is listening to it's port?

Check open ports with
```

netstat -a | grep LISTEN
lsof -i

```

---

### Post by pk_volt on 2006-01-15
[QUOTE=Mr_Grieves]Have you verified that swat is listening to it's port?

Check open ports with
```

netstat -a | grep LISTEN
lsof -i

```[/QUOTE]

hhmm, id on't see anything with port 901 if that's what I'm suppose to be looking for.

---

