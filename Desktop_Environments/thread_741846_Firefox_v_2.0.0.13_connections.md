---
title: "Firefox v 2.0.0.13 connections"
date: 2008-04-01
forum: Desktop Environments
---

### Post by jmore9 on 2008-04-01
Hello!
I am just wondering why firefox would have 4 active connections when onlu 1 browser window open and onlu 1 user.Seems like it would only need 1 connection not 4.  thank in advance for any info

---

### Post by SanskritFritz on 2008-04-01
[http://kb.mozillazine.org/Network.http.pipelining.maxrequests](http://kb.mozillazine.org/Network.http.pipelining.maxrequests)
Note the default value = 4.

---

### Post by jmore9 on 2008-04-01
ok thanks.  Did not understand what that link meant but thanks anyway.  The 4 connections were all going to the same address from the same origination.  but again thanks anyway

---

### Post by SanskritFritz on 2008-04-01
Exactly, the 4 connections mean, that Firefox uses 4 threads to download the contents of the webpage. You can incease of decrease them to gain speed or responsiveness, that is my link about, just for explanation.

---

