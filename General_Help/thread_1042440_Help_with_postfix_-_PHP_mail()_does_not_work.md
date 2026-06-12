---
title: "Help with postfix - PHP mail() does not work"
date: 2009-01-17
forum: General Help
---

### Post by scott29 on 2009-01-17
Hi,

I am having a terrible time getting postfix to work.  I am not sure if I have some incorrect settings, or something is not right in my hosts file.

The specific issue is with a plugin for Wordpress (Quick SMS).  Basically the text messages are not being sent.  In the mail.log I see the following regarding timeouts.  An excerpt is below - note I took out my domain name and cell number for the text message email address.  

Any ideas on what settings I may need to look at to get this working?

Jan 17 09:33:10 scottlinux postfix/local[29340]: 5FDB07CA326: to=<scott@mydomain>, relay=local, delay=977, delays=977/0.01/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Jan 17 09:33:10 scottlinux postfix/qmgr[29336]: 5FDB07CA326: removed
Jan 17 09:33:40 scottlinux postfix/smtp[29341]: connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out
Jan 17 09:33:40 scottlinux postfix/smtp[29341]: B5FBB7CA324: to=<XXXXXXXXXX@txt.att.net>, relay=none, delay=1075, delays=1045/0.01/30/0, dsn=4.4.1, status=deferred (connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out)
Jan 17 09:33:45 scottlinux postfix/pickup[29334]: A30577CA327: uid=33 from=<www-data>
Jan 17 09:33:45 scottlinux postfix/cleanup[29419]: A30577CA327: message-id=<20090117153345.A30577CA327@scottlinux.mydomain>
Jan 17 09:33:45 scottlinux postfix/qmgr[29336]: A30577CA327: from=<www-data@scottlinux.mydomain>, size=339, nrcpt=1 (queue active)
Jan 17 09:34:15 scottlinux postfix/smtp[29341]: connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out

Thank You!

---

### Post by scott29 on 2009-01-17
If there is another board better suited to this question please let me know.

---

### Post by dcstar on 2009-01-17
> **scott29 said:**
> Hi,

I am having a terrible time getting postfix to work.  I am not sure if I have some incorrect settings, or something is not right in my hosts file.

The specific issue is with a plugin for Wordpress (Quick SMS).  Basically the text messages are not being sent.  In the mail.log I see the following regarding timeouts.  An excerpt is below - note I took out my domain name and cell number for the text message email address.  

Any ideas on what settings I may need to look at to get this working?

Jan 17 09:33:10 scottlinux postfix/local[29340]: 5FDB07CA326: to=<scott@mydomain>, relay=local, delay=977, delays=977/0.01/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Jan 17 09:33:10 scottlinux postfix/qmgr[29336]: 5FDB07CA326: removed
Jan 17 09:33:40 scottlinux postfix/smtp[29341]: connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out
Jan 17 09:33:40 scottlinux postfix/smtp[29341]: B5FBB7CA324: to=<XXXXXXXXXX@txt.att.net>, relay=none, delay=1075, delays=1045/0.01/30/0, dsn=4.4.1, status=deferred (connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out)
Jan 17 09:33:45 scottlinux postfix/pickup[29334]: A30577CA327: uid=33 from=<www-data>
Jan 17 09:33:45 scottlinux postfix/cleanup[29419]: A30577CA327: message-id=<20090117153345.A30577CA327@scottlinux.mydomain>
Jan 17 09:33:45 scottlinux postfix/qmgr[29336]: A30577CA327: from=<www-data@scottlinux.mydomain>, size=339, nrcpt=1 (queue active)
Jan 17 09:34:15 scottlinux postfix/smtp[29341]: connect to atlsmtp.cingularme.net[66.102.165.114]:25: Connection timed out

Thank You!

You need to manually test the connection doing the following:

```
telnet atlsmtp.cingularme.net 25
```

If it doesn't connect then there is something blocking it (BTW, I can connect to it).

If your ISP blocks port 25 to external destinations, then you may need to put your ISP's SMTP server address as the postfix relay.

---

### Post by scott29 on 2009-01-18
Hi,

Thanks for the reply.  I added my ISP's smtp server as the relayhost.  That seems to have gotten my further, but now I'm getting a new error that says "530 authentication required". 

Is there something I can put in the Postfix main.cf to handle this, or is it more complicated?

Thank You
Scott29

---

### Post by scott29 on 2009-01-19
Just a bump to see if anybody saw this or can let me know about how to handle the authentication part.

Thanks.

---

