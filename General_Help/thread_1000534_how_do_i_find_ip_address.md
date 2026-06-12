---
title: "how do i find ip address"
date: 2008-12-03
forum: General Help
---

### Post by alwayshere on 2008-12-03
how do i find ip address of a website

---

### Post by amauk on 2008-12-03
easiest is using
```
nslookup www.website.com
```

---

### Post by alwayshere on 2008-12-03
it said 
 
           ** server can't find [http://www.google.co.nz/:](http://www.google.co.nz/:) SERVFAIL

im trying to find ip  for [http://www.google.co.nz/](http://www.google.co.nz/) 
so i can set it as home page 

im currently using [http://209.85.171.100/](http://209.85.171.100/)
as my home page but i want  the nz one (New Zealand )

setting home page this way loads it realy fast!!!

can anyone help me to find [http://www.google.co.nz/](http://www.google.co.nz/)  
ip

---

### Post by amauk on 2008-12-03
don't put http:// in front

nslookup [www.google.co.nz](www.google.co.nz)

*edit*

what you're doing may not work with google
as they use [round-robin DNS records]("http://en.wikipedia.org/wiki/Round_robin_DNS")

You'll always be pointed to the least busy, local IP address
(compare results from other suffixes - .co.uk, .co.fr, .com - they'll get the same results)

---

### Post by deadowl on 2008-12-03
You could use wireshark to listen on your network interface when you go to the website.
Firestarter also shows a list of active connections, but wireshark would probably suit you as a tool better.

---

