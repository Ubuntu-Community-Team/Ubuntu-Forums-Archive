---
title: "Odd Sendmail Problem"
date: 2009-01-29
forum: General Help
---

### Post by andy_gto on 2009-01-29
I'm stumped as to where to go from here.  Any time I send email, the logs say that it's sending to [email]username@www.domain.com[/email]

Jan 29 13:08:27 my_server sendmail[15015]: n0TL8QYv015015: to=andy.gtp@domain.com, ctladdr=nagios (1002/1002), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30219, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (n0TL8Q4u015016 Message accepted for delivery)

Jan 29 13:08:27 my_server sm-mta[15018]: n0TL8Q4u015016: to=<andy.gto@www.domain.com>, ctladdr=<nagios@server.ad.domain.com> (1002/1002), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=120549, relay=exchange.ad.domain.com. [172.18.201.151], dsn=5.7.1, stat=User unknown

I'm trying to figure out why it's adding the www to my email address through sm-mta?  If anyone has suggestions, I'd be very grateful!

Thanks!

---

### Post by dcstar on 2009-01-29
> **andy_gto said:**
> I'm stumped as to where to go from here.  Any time I send email, the logs say that it's sending to [email]username@www.domain.com[/email]

Jan 29 13:08:27 my_server sendmail[15015]: n0TL8QYv015015: to=andy.gtp@domain.com, ctladdr=nagios (1002/1002), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30219, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (n0TL8Q4u015016 Message accepted for delivery)

Jan 29 13:08:27 my_server sm-mta[15018]: n0TL8Q4u015016: to=<andy.gto@www.domain.com>, ctladdr=<nagios@server.ad.domain.com> (1002/1002), delay=00:00:01, xdelay=00:00:00, mailer=relay, pri=120549, relay=exchange.ad.domain.com. [172.18.201.151], dsn=5.7.1, stat=User unknown

I'm trying to figure out why it's adding the www to my email address through sm-mta?  If anyone has suggestions, I'd be very grateful!

Thanks!

I can't help you with sendmail setup, but I can tell you that the postfix MTA is nice and simple to setup and get going.

Unless you have a specific reason for using sendmail, it may be worth trying.

---

