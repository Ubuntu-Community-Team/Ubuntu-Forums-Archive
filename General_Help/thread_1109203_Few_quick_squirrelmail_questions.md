---
title: "Few quick squirrelmail questions"
date: 2009-03-28
forum: General Help
---

### Post by linuxisevolution on 2009-03-28
I bought the domain directoryadmin.info and the subdomain mail.directoryadmin.info . I set up a virtual host in apache as follows:
```

<VirtualHost *>
 ServerName mail.directoryadmin.info
 ServerAlias mail.*
 ServerAdmin  winrid@directoryadmin.info
 DocumentRoot  /usr/share/squirrelmail
 </VirtualHost>

```

**1. Is this correct?** I also install courier-imap. I setup the mail.directoryadmin.info to my server's ip address.

**2. Where is squirrel mail's document root??** Is it /usr/share/squirrelmail?

**3. Can I access my squirrelmail without waiting for my domain to register?**

Thanks! I finally won't have to use Yahoo anymore :)

---

### Post by linuxisevolution on 2009-03-28
Ok, its all working now. I got the answers to my questions my self :KS

But I get the error:

ERROR: Connection dropped by IMAP server.
:(

---

