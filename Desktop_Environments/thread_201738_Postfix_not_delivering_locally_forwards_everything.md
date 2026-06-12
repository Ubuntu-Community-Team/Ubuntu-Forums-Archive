---
title: "Postfix not delivering locally: forwards everything thru relayhost"
date: 2006-06-22
forum: Desktop Environments
---

### Post by jabster on 2006-06-22
Hi.

I seem to have encountered a bit of a problem with my mail server (k/ubuntu dapper, fresh install).

I was having trouble relaying thru sbcglobal.net, and found some info, and thought all was fixed. Now tho, I can not deliver locally, and everything fetchmail grabs seems to be re-relayed back thru the sbc servers. If I'm reading the log correctly.

Relevant files are below. If more is needed, just ask.

Thanks,
john

/etc/postfix/main.cf
```
smtpd_banner = $myhostname ESMTP $mail_name (Kubuntu Dapper Linux)
biff = no
append_dot_mydomain = no
myhostname = icculus.jabster.net
mydomain = jabster.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
#relayhost = 
#mynetworks = 127.0.0.0/8
#mailbox_command = /usr/bin/procmail -a "$EXTENSION"
#mailbox_command = /usr/bin/procmail -Y -a $DOMAIN
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
mynetworks_style = class
relayhost = [smtp.sbcglobal.yahoo.com]
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = 
smtp_sasl_password_maps = hash:/etc/postfix/saslpass
transport_maps = hash:/etc/postfix/transport

```

/var/log/mail.log
```
Jun 22 07:19:11 icculus postfix/smtp[7868]: B56144467A: to=<myaddress@sbcglobal.net>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=2, status=sent (250 ok 1150978749 qp 87418)
Jun 22 07:19:11 icculus postfix/qmgr[7861]: B56144467A: removed
Jun 22 07:19:39 icculus fetchmail[7828]: 1 message for myaddress@sbcglobal.net at pop.sbcglobal.yahoo.com (2031 octets). 
Jun 22 07:19:40 icculus fetchmail[7828]: reading message myaddress@sbcglobal.net@pop-sbc.mail.yahoo4.akadns.net:1 of 1 (1614 octets) 
Jun 22 07:19:40 icculus postfix/smtpd[7864]: connect from localhost.localdomain[127.0.0.1]
Jun 22 07:19:40 icculus postfix/smtpd[7864]: 1CBD34467A: client=localhost.localdomain[127.0.0.1]
Jun 22 07:19:40 icculus postfix/cleanup[7867]: 1CBD34467A: message-id=<200606220719.08922.jabster@jabster.net>
Jun 22 07:19:40 icculus postfix/qmgr[7861]: 1CBD34467A: from=<jabster@jabster.net>, size=2003, nrcpt=1 (queue active)
Jun 22 07:19:40 icculus fetchmail[7828]:  flushed 
Jun 22 07:19:40 icculus postfix/smtpd[7864]: disconnect from localhost.localdomain[127.0.0.1]
Jun 22 07:19:41 icculus postfix/smtp[7868]: 1CBD34467A: to=<johnj@localhost>, relay=smtp.sbc.mail.yahoo4.akadns.net[68.142.198.11], delay=1, status=sent (250 ok 1150978780 qp 75758)
Jun 22 07:19:41 icculus postfix/qmgr[7861]: 1CBD34467A: removed
Jun 22 07:20:00 icculus fetchmail[7828]: terminated with signal 15 
```

---

