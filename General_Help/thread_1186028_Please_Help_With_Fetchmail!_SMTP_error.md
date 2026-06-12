---
title: "Please Help With Fetchmail! SMTP error"
date: 2009-06-12
forum: General Help
---

### Post by MetapostAddict on 2009-06-12
Hi all,
 
I'm bleary eyed from spending an entire day trying to fix an error I get when I run fetchmail. I keep getting an "smtp listener protocol error" message. I just can't seem to find any helpful information. The full fetchmail output is as follows. thanks in advance for any help 
I have sendmail, openssl, and other such porgrams installed.
 
Please help!
Thanks

---

### Post by dcstar on 2009-06-13
> **MetapostAddict said:**
> Hi all,

I'm bleary eyed from spending an entire day trying to fix an error I get when I run fetchmail.  I keep getting an "smtp listener protocol error" message.  I just can't seem to find any helpful information.  The full fetchmail output is as follows.  thanks in advance for any help!





If i telnet port 25 I get



I have sendmail, openssl, and other such porgrams installed.

Please help!
Thanks

1) Please DON'T "Quote" code - use the CODE function.

2) Find out why Sendmail does not work:

```
fetchmail: SMTP< 421 **4.3.0 collect: Cannot write** ./dfn5D2s21r020140 (bfcommit, uid=0, gid=126): No such file or directory
fetchmail: SMTP error: 421 **4.3.0 collect: Cannot write** ./dfn5D2s21r020140 (bfcommit, uid=0, gid=126): No such file or directory
```

---

### Post by jonobr on 2009-06-13
Im not sure if this is relevant, but your fetchmail info shows its using  SMTP,

however, your telnet localhost shows its an ESTMP server (extended SMTP server) which adds additional security authentication and control.

Im not used to looking at the output of fetchmail so again, not sure if this is relevant

---

