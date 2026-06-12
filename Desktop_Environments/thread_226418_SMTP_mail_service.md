---
title: "SMTP mail service"
date: 2006-07-31
forum: Desktop Environments
---

### Post by zoon_unit on 2006-07-31
I have a LAMP ubuntu install and I want to enable an email service for email testing.

Can anyone tell me the best way to do this?

Thanks from a newbie!

---

### Post by zoon_unit on 2006-08-01
I'm still hoping someone can help me figure out how to activate SMTP email on my LAMP install of Ubuntu!

I figure it must be something simple, but I can't find it.

Thanks!

---

### Post by endfx on 2006-08-01
All I can point you to is:
packages.ubuntu.com

and search for smtp.

That lists all the smtp services that can be installed.
I think you are interested in smtpd -> This will install:

1) smtpd which listens for incoming mail
2) sendmail (if you don't already have it) which will allow you to send emails.

Here is the link for the package description:
[http://packages.ubuntu.com/dapper/mail/smtpd](http://packages.ubuntu.com/dapper/mail/smtpd)

If this is what you want, just do a:
sudo apt-get update
sudo apt-get install smtpd

Is this what you want?

---

