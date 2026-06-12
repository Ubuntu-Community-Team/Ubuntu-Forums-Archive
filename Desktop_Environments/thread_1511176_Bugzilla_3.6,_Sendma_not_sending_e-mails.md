---
title: "Bugzilla 3.6, Sendma not sending e-mails"
date: 2010-06-16
forum: Desktop Environments
---

### Post by tmor on 2010-06-16
Having trouble getting Bugzilla 3.6 to send notification e-mails via sendmail on Ubuntu 10.4.  I haven't been able to find anything on how to even diagnose this problem.  Simply, I'm not getting e-mails - 2+2 is not equaling 4.

running:
./checksetup.pl
yields no information. It tells me everything is good, it creates my tables and gives out no errors.

My web server, Apache2, is accessible and running.  Same with the MySQL database. Phpmyadmin works fine.  I can access my bugzilla site perfectly at [http://localhost/bugzilla](http://localhost/bugzilla)

It'll let me sign in fine and create a bug, but I cannot do any e-mail related activities.

Thanks in advance.

Ty

---

### Post by tr333 on 2010-09-03
I assume you got exim4 installed automatically when you installed bugzilla3 via apt?

You probably need to reconfigure the exim4-config package to setup exim4 for sending emails.

```
$ sudo dpkg-reconfigure exim4-config
```

If you have another mail server on your network that normally handles sending e-mails, you can configure exim4 to send mail through a smarthost and specify the mail server as the outgoing smarthost.  Also make sure the **mail_delivery_method** in e-mail parameters is set to sendmail (exim4 provides /usr/sbin/sendmail).

---

