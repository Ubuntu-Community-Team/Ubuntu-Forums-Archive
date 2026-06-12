---
title: "how to prevent a domain from being resolved?"
date: 2009-02-13
forum: General Help
---

### Post by googlorenz on 2009-02-13
hello,

is there a way to prevent a specific domain from being resolved?
I know that I can use the /etc/hosts file to assign a wrong ip-address to it, but I want that the domain cannot be resolved at all, as if it did not exist.


thank you for your help!

EDIT: I am using Ubuntu 8.04 amd64 Server Edition.

---

### Post by jonobr on 2009-02-13
Just curious what the problem with using the host file is.

The name will have to resolve against something and the first place it usually goes is to the hosts file and then to dns.

If its a network traffic generation thing, its only tiny, but can be stopped by mapping eg banned.domain.com to 127.0.0.1
Which means it goes to the loopback and doesnt hit the network.

---

### Post by googlorenz on 2009-02-13
well, using 127.0.0.1 as ip in the hostfile works. however, i want to fool an application into thinking, that the domain it tries to reach does not exist, because it will not work properly if it thinks that the domain exists but the server happens to be down...

---

### Post by jonobr on 2009-02-13
I may be wrong, but that kind of functionality should reside in your application?


ONce it gets outside the application, the machine just uses it config to find out who to ask next.

Ie. I have to resolve this, do you know who this is? No, ok, do you know who this is? No, ok- Firefox, it doesnt exist.

However, each time your machine will look for that address.

---

### Post by googlorenz on 2009-02-13
i understand this mechanism. i would like to configure the machine to believe that the domain does not exist, without even looking up the domain.
so:
I have to resolve this, do you know who this is?
No! (without even asking the nameservers)
Application, it doesnt exist.

---

