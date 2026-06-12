---
title: "static wired connection fails / must add route gateway"
date: 2009-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rioguia on 2009-08-30
My 9.04 Ubuntu wired connection appears to be fine when I look at the configuration files and gui interfaces.  It will ping my network fine  and query dig successfully but no other services work.  After I open a terminal and 

route -n shows no gateway 

sudo route add default gw xxx.xxx.xxx.xxx (my route IP)

Then all services work fine.

What am I doing wrong?

---

### Post by rioguia on 2009-12-07
I have since updated to Ubuntu 9.10, hoping it would solve my problem.  It didn't.

I figured out why the wireless Gateway setting disappeared and the difficulties I encountered making WEP work using the Network Manager.  I posted my notes and screen shots on all the tabs for the Network Manager at [Ubuntu Wireless WEP with Static IP]("http://www.substantis.com/blog/?p=87").  

In sum, WEP worked when I used the security settings for 40/128 bit key and authentication type &#8220;open&#8221; (instead of shared). I cured the &#8220;blank&#8221; or disappearing default gateway problem by hitting the enter key after typing the gateway setting (while the gateway field is still active).

---

