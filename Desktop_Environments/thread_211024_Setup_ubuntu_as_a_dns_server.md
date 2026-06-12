---
title: "Setup ubuntu as a dns server?"
date: 2006-07-07
forum: Desktop Environments
---

### Post by geuis on 2006-07-07
I'm the IT manager for a small company. We're an all-Windows network but I run ubuntu at home on a spare pc.

I want to setup a DNS server that we can run from our corporate office that will only allow certain websites that we define to be accessed. I've already got the router issue taken care of, i.e. once we do this any DNS requests leaving our various stores will be redirected to our master DNS server, even if they change the DNS server settings on the remote workstations.

What packages do I need to install onto my server machine in Ubuntu to get a good DNS system going? Also, can someone point me to requisite walkthroughs on how to configure the server to only allow access to our whitelist of websites?

Thanks,

Geuis

---

### Post by PingunZ on 2006-07-07
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Grtz PingunZ

---

### Post by lamego on 2006-07-07
BIND is probably the most used dns server software, just install it with:
```
sudo apt-get install bind
```

---

### Post by fnkhan on 2008-03-20
after bind install wat can i do my system ip is 192.168.0.81 and host name is ubuntu plz send me the configuration. I have another problem nslookup and dig command is not working the error is command not found plz tell me wat can i do.:confused:

---

