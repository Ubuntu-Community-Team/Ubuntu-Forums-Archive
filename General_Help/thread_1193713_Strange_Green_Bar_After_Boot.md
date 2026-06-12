---
title: "Strange Green Bar After Boot"
date: 2009-06-21
forum: General Help
---

### Post by AdvidInternetPerson on 2009-06-21
Hello World of Ubuntu,

Let me get straight to the point: Each time I boot 9.04 I get a strange green bar (see picture). This happened after I reconnected my computer from my TV to my monitor. I have already tried several methods, such as restoring the xorg.conf file. The computer fully starts though. I can ping the computer and accesses all shared files. I have googled for answers for many hours, but to no avail. 

Specs:
Core 2 Duo
945GTC-m
2gb RAM 
ATI HD3650 1gb DDR2

Please help a fellow user out! Thanks.

---

### Post by Johnny B on 2009-06-21
i recently fixed a computer that had this problem, boot the recovery mode and:

# sudo apt-get remove xorg-driver-fglrx

*edit: not guaranteed to work!
it could be something else all together.

---

### Post by AdvidInternetPerson on 2009-06-21
Wow, one easy fix. Thanks so much!

---

