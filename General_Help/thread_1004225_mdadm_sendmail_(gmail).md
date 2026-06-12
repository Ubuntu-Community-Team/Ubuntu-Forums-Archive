---
title: "mdadm sendmail (gmail)"
date: 2008-12-07
forum: General Help
---

### Post by BassKozz on 2008-12-07
I just recently setup my very 1st software RAID array thanks to this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

And I'd like to setup sendmail so that I can get email alerts (should something go wrong), currently when I run a test I get the following:
```
mdadm: metadata format 00.90 unknown, ignored.
sh: /usr/sbin/sendmail: not found
```

Most of the info on this topic relates to using postfix. But after spending the past 24hrs trying to get postfix setup using Gmail and these tutorials:
[LIST]
[*][http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html](http://prantran.blogspot.com/2007/01/getting-postfix-to-work-on-ubuntu-with.html)
[*][http://bookmarks.honewatson.com/2008/04/20/postfix-gmail-smtp-relay/](http://bookmarks.honewatson.com/2008/04/20/postfix-gmail-smtp-relay/)
[*][http://souptonuts.sourceforge.net/postfix_tutorial.html](http://souptonuts.sourceforge.net/postfix_tutorial.html)
[/LIST]
and getting no where FAST I am looking for something else, a SIMPLE solution that I can use to send mail using gmail.
I believe the problem I've run into with these various guides are related to the server certificate not working, according to my */var/log/mail.log*:
```
Dec  7 01:05:45 Unicorn-NAS postfix/master[5017]: reload configuration /etc/postfix
Dec  7 01:07:50 Unicorn-NAS postfix/pickup[5694]: ADF85A2E07A: uid=1000 from=<user>
Dec  7 01:07:50 Unicorn-NAS postfix/cleanup[5899]: ADF85A2E07A: message-id=<20081207060750.ADF85A2E07A@Unicorn-NAS.localdomain>
Dec  7 01:07:50 Unicorn-NAS postfix/qmgr[5695]: ADF85A2E07A: from=<user@Unicorn-NAS.localdomain>, size=314, nrcpt=1 (queue active)
Dec  7 01:07:51 Unicorn-NAS postfix/smtp[5901]: certificate verification failed for smtp.gmail.com[209.85.133.109]:587: untrusted issuer /C=ZA/ST=Western Cape/L=Cape Town/O=Thawte Consulting cc/OU=Certification Services Division/CN=Thawte Premium Server CA/emailAddress=premium-server@thawte.com
Dec  7 01:07:53 Unicorn-NAS postfix/smtp[5901]: ADF85A2E07A: to=<basskozz@myemail.com>, relay=smtp.gmail.com[209.85.133.109]:587, delay=2.4, delays=0.03/0.24/1/1.1, dsn=2.1.5, status=deliverable (250 2.1.5 OK d21sm16248940and.46)
Dec  7 01:07:53 Unicorn-NAS postfix/cleanup[5899]: 24DBFA2E07B: message-id=<20081207060753.24DBFA2E07B@Unicorn-NAS.localdomain>
Dec  7 01:07:53 Unicorn-NAS postfix/bounce[5904]: ADF85A2E07A: sender delivery status notification: 24DBFA2E07B
Dec  7 01:07:53 Unicorn-NAS postfix/qmgr[5695]: ADF85A2E07A: removed
Dec  7 01:07:53 Unicorn-NAS postfix/qmgr[5695]: 24DBFA2E07B: from=<>, size=1959, nrcpt=1 (queue active)
Dec  7 01:07:53 Unicorn-NAS postfix/local[5905]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Dec  7 01:07:53 Unicorn-NAS postfix/local[5905]: 24DBFA2E07B: to=<user@Unicorn-NAS.localdomain>, relay=local, delay=0.07, delays=0.01/0.01/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Dec  7 01:07:53 Unicorn-NAS postfix/qmgr[5695]: 24DBFA2E07B: removed
```
I've tried everything, I can't seem to get this working...

There has got to be an easier solution to this?

After some googling I came across **msmtp** and **ssmtp**, can I use one of these?  What is the EASIEST solution to get sendmail up and running thru Gmail?
TiA,
-BassKozz

---

### Post by BassKozz on 2008-12-07
Nevermind, I found an easy solution using exim4: [http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/](http://www.manu-j.com/blog/wordpress-exim4-ubuntu-gmail-smtp/75/)

No CA Certs Required :D

---

