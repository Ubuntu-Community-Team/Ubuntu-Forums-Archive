---
title: "apt install bind9 - cannot start DNS"
date: 2009-01-21
forum: General Help
---

### Post by MN Noob on 2009-01-21
I just installed Ubuntu 8.10 Server over the weekend. Everything was working fine. Then yesterday I got an error, I think it was rndc...prot 953. Then today, I was using webmin and I stopped bind, and tried to start it back up and it said it couldn't. Instead of trying to troubleshoot the actual problem I did apt-get remove bind9. Then I tried installing again. It gets through the install, but when it tries to start bind it says
* starting DNS...bind9...fail!
So I go to /etc/bind and there is only one file, rndc.key. I did a whereis and it says /etc/bind.

How can I fix this, or how I can I completely remove bind from my system and start over.

---

