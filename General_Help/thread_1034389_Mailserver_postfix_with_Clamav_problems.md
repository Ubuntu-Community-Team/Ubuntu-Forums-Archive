---
title: "Mailserver postfix with Clamav problems"
date: 2009-01-08
forum: General Help
---

### Post by Peque on 2009-01-08
Hery Guys. 

After updating my Mailserver to latyest packages I've runned into this problem with my mailscanner: 

```
Jan  8 15:27:18 sif amavis[11666]: (11666-01-4) (!)PRESERVING EVIDENCE in /var/lib/amavis/tmp/amavis-20090108T152713-11666
Jan  8 15:27:18 sif postfix/smtp[11598]: 6B850150561: to=<rita@ritajuul.dk>, relay=127.0.0.1[127.0.0.1]:10024, conn_use=4, delay=101126, delays=101071/50/0/4.3, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 Error in processing, id=11666-01-4, quar+notif FAILED: temporarily unable to quarantine: 451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/o/spam-oYp7417aseoU.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98., id=11666-01-4 at /usr/sbin/amavisd-new line 10371. (in reply to end of DATA command))
Jan  8 15:27:19 sif amavis[11676]: (11676-01-2) (!)451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/i/spam-iYAwyhcW2mEq.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98.
Jan  8 15:27:19 sif amavis[11676]: (11676-01-2) (!!)TROUBLE in check_mail: quar+notif FAILED: temporarily unable to quarantine: 451 4.5.0 Local delivery(1) to /var/lib/amavis/virusmails/i/spam-iYAwyhcW2mEq.gz failed: Can't call method "value" on an undefined value at /usr/share/perl5/IO/Compress/RawDeflate.pm line 98., id=11676-01-2 at /usr/sbin/amavisd-new line 10371.
```

What is the problem / solution for the different method that is not known to the system ???

---

