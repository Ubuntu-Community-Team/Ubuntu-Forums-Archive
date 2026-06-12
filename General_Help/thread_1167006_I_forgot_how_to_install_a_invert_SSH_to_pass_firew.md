---
title: "I forgot: how to install a invert SSH to pass firewall, port 80?"
date: 2009-05-22
forum: General Help
---

### Post by frenchn00b on 2009-05-22
Hello,
 
Once I had all info to do so.

Server ssh is being a firewall, only port 80 is allowed.

there is hte invert SSH package, what s hte name, how to get it working please?

thansk

---

### Post by HermanAB on 2009-05-22
Howdy,

Install the ssh server package.  Modify /etc/ssh/sshd_config.  Change Port 22 to Port 80 and restart service.  Then connect to it using:
$ ssh user@server -p 80

---

### Post by frenchn00b on 2009-05-22
> **HermanAB said:**
> Howdy,

Install the ssh server package.  Modify /etc/ssh/sshd_config.  Change Port 22 to Port 80 and restart service.  Then connect to it using:
$ ssh user@server -p 80

no no there is  a special tar.gz for that

the name has HTTP in ... 
can recall ... :(

---

### Post by frenchn00b on 2009-05-22
> **frenchn00b said:**
> no no there is  a special tar.gz for that

the name has HTTP in ... 
can recall ... :(

almost :

[http://pentestmonkey.net/tools/perl-reverse-shell/](http://pentestmonkey.net/tools/perl-reverse-shell/)

---

### Post by frenchn00b on 2009-05-22
Found !!

[http://matahari.sourceforge.net/](http://matahari.sourceforge.net/)

---

