---
title: "Apache Web server help"
date: 2009-03-10
forum: General Help
---

### Post by unplugged23 on 2009-03-10
Hey there,

I thought I'd give hosting my own web server a go, I have apache, php, mysql, and mysql admin installed. I'm also using rapache, so I can see what I'm doing. I've never really hosted a webserver before, but I understand html, and a slight bit of php. I know what mysql is for but I havent gotten around to learning it yet. Any ways, my question is how do I get the apache server on the internet? I can connect to my site and see that I'm succesfully making changes to it from localhost, but say I'm not on my house computer, what would I need to connect to? I would assume its my static ip, but I dont know how to get or configure apache to run with that. Thanks in advance for the help. :D

---

### Post by GCoffee on 2009-03-10
you would need to forward your ports, to do this go to:

[http://192.168.1.1](http://192.168.1.1) (Normal)
[http://192.168.0.1](http://192.168.0.1) (Netgear Routers)

typically the password is something like password or admin if you havent changed it (you should) and the username is almost always admin or administrator. Forwarding will be under something like firewall and the service would be http, ftp and i think SQL but im not sure about the last one, you could always make your own under a option like services.

Unless you wanted people typing in raw ip addresses (172.125.312.123 ETC)
you want to get a hostname as well, you can get one free from: no-ip.com or dyndns.com. if you have a dynamic ip (which you most probably will) then you will need to download the linux updater as well, i think one if not both have one.

Hope this helped.

GCoffee.

---

### Post by mcla0203 on 2009-03-10
Register a DNS.  Domain Name Service.  It associates a URL to your static ip.  You then have to tell apache what your Domain name is, ie google.com is one.  This is usually inside the an apache config file called apache2.conf in the default /etc/apache2 directory.  So if the domain you use is example.com, then you would write example.com inside the apache2.conf file.  It actually looks like this:


```

DocumentRoot "/home/your_user_name/www"  
ServerName "csref.info:80"
```

DocumentRoot tells apache where the html files are.  It is web root.
ServerName is the Domain you registered through a DNS provider.

You'll have to check a number of other things too, but this is a start.

---

### Post by unplugged23 on 2009-03-10
> **GCoffee said:**
> you would need to forward your ports, to do this go to:

[http://192.168.1.1](http://192.168.1.1) (Normal)
[http://192.168.0.1](http://192.168.0.1) (Netgear Routers)

typically the password is something like password or admin if you havent changed it (you should) and the username is almost always admin or administrator. Forwarding will be under something like firewall and the service would be http, ftp and i think SQL but im not sure about the last one, you could always make your own under a option like services.

Unless you wanted people typing in raw ip addresses (172.125.312.123 ETC)
you want to get a hostname as well, you can get one free from: no-ip.com or dyndns.com. if you have a dynamic ip (which you most probably will) then you will need to download the linux updater as well, i think one if not both have one.

Hope this helped.

GCoffee.

Helped a bunch, I'll get working on it in a bit. I'll let you know if i run into any trouble. Thanks Again! :D

---

### Post by unplugged23 on 2009-03-10
> **mcla0203 said:**
> Register a DNS.  Domain Name Service.  It associates a URL to your static ip.  You then have to tell apache what your Domain name is, ie google.com is one.  This is usually inside the an apache config file called apache2.conf in the default /etc/apache2 directory.  So if the domain you use is example.com, then you would write example.com inside the apache2.conf file.  It actually looks like this:


```

DocumentRoot "/home/your_user_name/www"  
ServerName "csref.info:80"
```

DocumentRoot tells apache where the html files are.  It is web root.
ServerName is the Domain you registered through a DNS provider.

You'll have to check a number of other things too, but this is a start.

Thanks, but don't I need to forward the ports first? I'm not sure, that's just what I would assume. :confused:

---

### Post by unplugged23 on 2009-03-10
How do I get get my system a static IP in ubuntu? Its looking like I'll need one to set this up properly.

---

### Post by unplugged23 on 2009-03-10
I don't think I'm using Dhcp, it looks like i have something called lo. when I go to edit the /etc/network/interfaces file, it shows ```
auto lo
iface lo inet loopback
``` and when i type *ip addr* in terminal I get something really wierd ```
ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:07:e9:78:48:53 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.101/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::207:e9ff:fe78:4853/64 scope link 
       valid_lft forever preferred_lft forever
3: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 42:92:4f:37:0f:2a brd ff:ff:ff:ff:ff:ff

```

Could anyone out there help me figure out what this means, and help me to get my static IP? Thanks for the help!

---

### Post by unplugged23 on 2009-03-10
Another question, after going a while of messing around with my site, now when I load my site from rapache, it gives me the directory "index of" sort of thing, instead of just my page. How can I change it so it just loads a page, and not a directory? :confused:

EDIT: it used to load just the page, instead of the directory.

---

