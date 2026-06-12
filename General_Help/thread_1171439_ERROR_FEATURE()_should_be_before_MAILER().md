---
title: "ERROR: FEATURE() should be before MAILER()"
date: 2009-05-27
forum: General Help
---

### Post by masimiqbal on 2009-05-27
Hi,
 
I am newbie in ubuntu, and _Configure sendmail for SMTP relay with my ISP. _i change my /etc/mail/sendmail.mc with these lines 
 
define(`SMART_HOST', `smtp.dsl.net.pk')
FEATURE(authinfo)dnl 
 
after change when i run this command 
 
" m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf "
 
the error is 
 
[FONT=Verdana]"*** ERROR: FEATURE() should be before MAILER() "[/FONT]
 
 
[FONT=Verdana]Can anyone help me to resolve this error[/FONT]

---

