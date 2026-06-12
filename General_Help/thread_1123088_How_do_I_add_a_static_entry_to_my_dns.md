---
title: "How do I add a static entry to my dns?"
date: 2009-04-11
forum: General Help
---

### Post by Linuxwho? on 2009-04-11
Here's what is there currently..(db.mydomain.com)

[B]"
;
; Bind data file for mydomain.com
;
$TTL    604800
@       IN      SOA     mail.mydomain.com. admin.mydomain.com. (
                        070725          ; Serial
                        604800          ; Refresh
                        86400           ; Retry
                        2419200         ; Expire
                        604800 )        ; Negative Cache TTL
;
@       IN      NS      mail
        IN      MX      10 mail
        IN      A       192.168.1.110
mail    IN      A       192.168.1.110[/B]

I want to add an entry for my server called "ubuntu.mydomain.com"  I guess it would be an "A" record.  Not sure how to do it correctly.

---

### Post by Wayne_V on 2009-04-11
Yes - you need to add an A record for each host.  You should also update the serial number each time you update your DNS.  Here's a good basic how-to:

[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)

---

### Post by Linuxwho? on 2009-04-11
> **Wayne_V said:**
> Yes - you need to add an A record for each host.  You should also update the serial number each time you update your DNS.  Here's a good basic how-to:

[http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml](http://news.softpedia.com/news/How-to-Host-Your-Own-Domain-With-Bind9-on-Ubuntu-49585.shtml)

Thanks.  Would it be fair to say add:

"ubuntu IN A 192.168.1.110" 

Like the following:
"[COLOR="Black"];
; Bind data file for mydomain.com
;
$TTL 604800
@ IN SOA mail.mydomain.com. admin.mydomain.com. (
070725 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
;
@ IN NS mail
IN MX 10 mail
IN A 192.168.1.110
mail IN A 192.168.1.110 [/COLOR]
[COLOR="DarkSlateBlue"]ubuntu IN A 192.168.1.110 [/COLOR]

---

### Post by dcstar on 2009-04-11
> **Linuxwho? said:**
> Here's what is there currently..(db.mydomain.com)
.......
        IN      A       192.168.1.110
mail    IN      A       192.168.1.110

I want to add an entry for my server called "ubuntu.mydomain.com"  I guess it would be an "A" record.  Not sure how to do it correctly.

You are using an internal network, if other machines do not access your server then a simple entry into your hosts file will suffice.

---

### Post by Linuxwho? on 2009-04-12
> **dcstar said:**
> You are using an internal network, if other machines do not access your server then a simple entry into your hosts file will suffice.

The problem is that my server is its own DNS server and when I run the host `hostname` command it comes back incorrectly.  I would like to try this and see if it works.  Do I have the entry correct 2 posts up?  Thanks.

Ultimately I am trying to solve below.  It should be coming back with my private IP NOT that 63.x or 8.x weird address..
"root@ubuntu:/etc# host `hostname`
ubuntu has address 63.251.179.13
ubuntu has address 8.15.7.117
Host ubuntu not found: 3(NXDOMAIN)
root@ubuntu:/etc#"

---

### Post by doas777 on 2009-04-12
My dns config does not use the "IN" keywords in the host entries.

they are all in the form of:
```

localhost  A        127.0.0.1

```

also i think you have too many bindings for mail.
if you want to add a name to an existing address, use a CNAME instead of A.
```
ns1        CNAME    13of2
```
this adds the name 'ns1' to the A entry for 13of2.

here is the header to my zone file. it omits some of the features your seems to be using.
```

$TTL 10

@ IN SOA 13of2.ABC.net. admin.ABC.net. (        
        20081213          ; serial
        8                 ; refresh
        2                 ; retry
        4W                ; expire
        1D                ; minimum
        )

  IN      NS  13of2.ABC.net.

localhost  A        127.0.0.1
...<other host entries>

```

---

### Post by doas777 on 2009-04-12
what do you see in your hostname file?
```
sudo gedit /etc/hostname
```

---

