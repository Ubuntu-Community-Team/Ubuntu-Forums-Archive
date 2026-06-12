---
title: "Temporary internet disabling software for Linux?"
date: 2009-11-05
forum: Desktop Environments
---

### Post by khughitt on 2009-11-05
Hi all,

I recently heard about [Freedom for Mac]("http://macfreedom.com/") which is basically a hack that lets you temporarily disable your internet connection, so that you can focus on work.

Anyone know if there is anything similar for Linux? So far I haven't been able to find any. The closest I've found are Firefox plugins, but that wouldn't do anything for email, chat, etc.

Any suggestions?

Thanks!

---

### Post by frederik.heremans on 2009-11-05
Just turn of your network-interface. Find the right one using ifconfig -a. Shutdown and statup an interface using:

```

ifdown eth0 

```
```

ifup eth0 

```

---

### Post by i.r.id10t on 2009-11-05
Execpt ifup/ifdown depend on the /etc/network/interfaces file which Ubuntu doesn't use for anything but lo :(

---

### Post by khughitt on 2009-11-05
> Just turn of your network-interface. Find the right one using ifconfig -a. Shutdown and statup an interface using:

Hehe.. that assumes I have the will power to resist re-enabling the connection before I get my work done :)

---

### Post by BbUiDgZ on 2009-11-05
> **pwnedd said:**
> Hehe.. that assumes I have the will power to resist re-enabling the connection before I get my work done :)

set a cron to run:
```
sudo /etc/init.d/networking stop
```

and then when u work is done assuming its a time
```
sudo /etc/init.d/networking start
```

---

