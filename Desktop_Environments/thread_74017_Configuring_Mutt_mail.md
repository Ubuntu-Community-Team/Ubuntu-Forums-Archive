---
title: "Configuring Mutt mail"
date: 2005-10-10
forum: Desktop Environments
---

### Post by dalani on 2005-10-10
I have made Mutt (the unix mail app) my default mail app in 5.04.
But whenever I send mail, the email get rejected because the default user domain is  not found (see messg below). Is there a way to set the From: ,Reply-To: and localdomain to a default address? And how do Iremedy the error shown below?

```
Diagnostic-Code: X-Postfix; host lycos-com.mr.outblaze.com[208.36.123.61] said:
    550 <steve@localhost.localdomain>: No thank you rejected: Domain not found
    (in reply to RCPT TO command)
```

---

### Post by multios on 2005-10-10
Make changes in your .muttrc

---

### Post by HermanAB on 2005-10-10
Edit this file:
/etc/Muttrc

There are tons of comments in the file.  You should be able to figure it out.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

