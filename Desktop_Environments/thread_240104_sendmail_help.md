---
title: "sendmail help"
date: 2006-08-20
forum: Desktop Environments
---

### Post by elj4176 on 2006-08-20
I've searched around a bit and haven't found the solution yet.

I'm trying to run phpffl for a fantasy football league this year and it uses the phpmail() function which in turn uses sendmail. The problem is that my ISP blocks anything but their domain name (earthlink.net) for smtp traffic.
I know it will work because I also run phpbb2 and had to specify my earthlink smtp server in order for the mailing functions to work in the forums.
I have tried running sendmailconfig and selecting Y for all 3 options and I have also tried answering Y to only the first and thrid prompts. The third prompt is asking ot restart sendmail. The relay-domains file has my earthlink mail server in it. 
I keep getting this error in my mail.log when a testuser signs up for phpffl and an auto email is sent :

Aug 20 09:44:36 localhost sendmail[31124]: k7KDiaQ0031124: from=www-data, size=292, class=0, nrcpts=0, msgid=<200608201344.k7KDiaQ0031124@localhost.localdomain>, relay=www-data@localhost

Sendmailconfig gives this error:

Creating /etc/mail/sendmail.cf...
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** MAILER(`local') must appear after FEATURE(`allmasquerade')*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** ERROR: FEATURE() should be before MAILER()
*** FEATURE(smrsh) must occur before MAILER(local)
*** ERROR: MAILER(local) already included
*** ERROR: MAILER(smtp) already included

Any help would be appreciated since the season will be starting soon.
My Evolution works fine for sending/receiving mail as does phpbb2.

THanks!

---

