---
title: "[SOLVED] gksudo takes almost a minute"
date: 2008-01-20
forum: Desktop Environments
---

### Post by x1a4 on 2008-01-20
Hi,

Ever since I installed Gutsy gksudo takes almost a minute before it validates the password, closes, and runs and application.  How can I diagnose and repair this problem?  

Thank you.

---

### Post by compiledkernel on 2008-01-20
look in  

/var/log/messages
/var/log/syslog 

I think also something might show up in 

/var/log/auth.log 

as well, but not certain. 

Something in those 3 should tell you whats goin on.

---

### Post by tears.of.angels on 2008-01-20
i had this problem when i upgraded as well.

i'm pretty sure my problem had to do with gksu grabbing the screen.

if you want to try that, run 

```
gksu-properties
```

from a terminal, and set grab mode to disable to see if that speeds it up.

---

### Post by x1a4 on 2008-01-26
> **tears.of.angels said:**
> i had this problem when i upgraded as well.

i'm pretty sure my problem had to do with gksu grabbing the screen.

if you want to try that, run 

```
gksu-properties
```

from a terminal, and set grab mode to disable to see if that speeds it up.

That did it.  Thank you.

---

