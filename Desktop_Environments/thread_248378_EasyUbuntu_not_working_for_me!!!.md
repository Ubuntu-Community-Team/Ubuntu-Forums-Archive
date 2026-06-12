---
title: "EasyUbuntu not working for me!!!"
date: 2006-09-01
forum: Desktop Environments
---

### Post by moufranica on 2006-09-01
Dear Gurus,
I have installed easyUbuntu, but I get errors as it seems easyubuntu can't get list of packages. 

```

http://packages.freecontrib.org/ubuntu/plf/dists/dapper/main/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/restricted/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/universe/binary-i386/Packages.gz: 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/multiverse/binary-i386/Packages.gz: 404 Not Found

```

---

### Post by matko on 2006-09-01
try change http: to ftp:

and paste here you /etc/apt.conf file

---

### Post by Uncle Spellbinder on 2006-09-01
See Here: [***_PLF ubuntu shutting down_***](http://plf.zarb.org/)

---

### Post by moufranica on 2006-09-01
> **matko said:**
> try change http: to ftp:

and paste here you /etc/apt.conf file

Here's my apt.conf:

```
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "203.81.71.234:8080";

```

---

