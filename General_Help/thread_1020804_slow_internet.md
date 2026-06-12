---
title: "slow internet"
date: 2008-12-24
forum: General Help
---

### Post by Howitzer777 on 2008-12-24
ok. i have windows virtualized. I love ubuntu but just one thing is the bothering me. the internet speed. I've tried countless browsers but still the same speed. i think it hangs on "looking up [site name]" but not sure.

i've tried the ipv6 thing and the firefox "about:config" edit

i didn't try dns caching but i don't think it will work. 


It's really bothering me. and I need at least an okay connection to be happy. help please?

i think its a problem with my network card and i may need drivers. but havent been able to find them on intel's site

Intel(R) 82566DC Gigabit Network Connection

---

### Post by HermanAB on 2008-12-24
You can test the DNS speed with 'dig' (Linux) and 'nslookup' (Linux/Windows).  Read the man pages for details - very simple stuff.  Once you found a fast DNS, put it at the top of the list in the Windows network wizard (and Ubuntu /etc/resolv.conf).

Cheers,

Herman

---

### Post by Howitzer777 on 2008-12-24
don't really understand what your saying. i checked my speed in linux and (i don't know anything about this stuff) it was 3770 kb/s down and 535 up

---

