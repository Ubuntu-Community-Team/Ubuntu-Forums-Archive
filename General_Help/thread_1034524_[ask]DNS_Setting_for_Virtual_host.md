---
title: "[ask]DNS Setting for Virtual host"
date: 2009-01-08
forum: General Help
---

### Post by c1m1n on 2009-01-08
Dear All,
I really need some suggestion.. I've already registered Three domain which are : pattel87.com, empang83.org and kapadubungsu.org from one of provider in my country. Unfortunately, i just have one public IP address 203.130.204.221. To host three domain,  i thought i should use name-based Virtual host, then i configured apache server on ubuntu to serve Vhost, Tried, configuring DNS like i found in this forum, locally i can connect to that vhost, but from internet can't. use dig for one of domain result like this:

; <<>> DiG 9.4.2-P2 <<>> pattel87.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 55856
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;pattel87.com.			IN	A

;; Query time: 3 msec
;; SERVER: 10.2.1.5#53(10.2.1.5)
;; WHEN: Fri Jan  9 08:43:33 2009
;; MSG SIZE  rcvd: 30

I think, the problem is about DNS setting. until now, i feel like facing with he big rocks. 
what i have supposed to do, the following attachment is our configuration file for examination..
really need help ..

Thanks you so much..
ARIF

---

