---
title: "godaddy domain hosting"
date: 2009-02-10
forum: General Help
---

### Post by userkiller on 2009-02-10
I wanted to now how can i created a domain like mike.com free.
can i hosted from my computer.

what is this thing call.
dns? is godaddy can do it i think i can do it:P:lolflag:.

i have 6 computers (new to ubuntu) and i want to turn:
1 for ftp 
2 for web (atleast 9 diffrent websites)
3 to host domain if that posible 
4-6 to host client side basicaly a dedicated server

Good or bad.

Also is there a way people can pay for web hosting( paying another company and they give me the money with out saving any info in my computer.

---

### Post by sandyd on 2009-02-10
its the dns isthe harder part. 
its best to use something like everydns.net for your dns.

But anyways...
first get an free subdomain at dyndns.org
point it to your ip

then point domain nameservers at that

type this into the computer you want to use to host the DNS
```

sudo apt-get install bind9

```webserver
```

sudo apt-get install apache2 php5 mysql-server

```ftp
```

sudo apt-get install pure-ftpd

```
now to give you some advice, heres a easy way to manage sites and servers.
download webmin ([http://prdownloads.sourceforge.net/webadmin/webmin_1.450_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.450_all.deb))
```

sudo dpkg -i webmin*.deb

```it might show dependency errors, so 

```

sudo apt-get -f install

```do that to ALL the computers

then you can go to http://<ipaddress of server>:10000
and manage each one.

P.S. the domain is also managed through webmin. Just go to Servers -> DNS 
Create a new zone 


you can also link all of them together, but thats in the webmin documentation

for 4 - 6
you can setup a ssh terminal for each computer (best to have different ip address for each, but whatever, doesn't really matter)

also setup webmin.
its easy for customers to use :)

---

### Post by sandyd on 2009-02-10
and could someone simplify this for me?
im pretty sure it works though...

---

