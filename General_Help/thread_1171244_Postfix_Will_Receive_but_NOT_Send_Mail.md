---
title: "Postfix Will Receive but NOT Send Mail"
date: 2009-05-27
forum: General Help
---

### Post by techy7636 on 2009-05-27
Hey All

I'm having problems with my Postfix setup - it will currently only send and receive through SquirrelMail but will only receive and NOT send via Outlook or other mail clients.

Every time I try to send I receive the following message:

Sending failed; Reason:554 5.7.1 : Relay access denied 

My config is set up as follows:

myhostname = mail.mydomainxxx.com
mynetworks_style = subnet
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mydomainxxx.com, $myhostname, localhost.$mydomain, localhost, $mydomain
relayhost =
mydomain = mydomainxxx.com
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination permit permit_inet_interfaces
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual
message_size_limit = 20480000
smtpd_sasl_security_options = 
inet_interfaces = all
inet_protocols = all
smtpd_sasl_auth_enable = yes

And my log records the following:

May 27 12:06:05 mydomainxxx postfix/smtpd[25959]: connect from sender1.othermail.com[72.5.230.103]
May 27 12:06:05 mydomainxxx postfix/smtpd[25959]: NOQUEUE: reject: RCPT from sender1.othermail.com[72.5.230.103]: 554 5.7.1 <other@yahoo.com>: Relay access denied; from=<rich@mydomainxxx.com> to=<other@yahoo.com> proto=ESMTP helo=<172.31.252.89>
May 27 12:06:06 mydomainxxx postfix/smtpd[25959]: disconnect from sender1.othermail.com[72.5.230.103]

Any help would be greatly appreciated,


Rich

---

### Post by LiQuidAiR on 2009-05-27
I had the very same problem.  It ended up being how outlook is trying to connect to your server.  It uses a connection method that is unknown to postfix.  Try using another mail client like Thunderbird.  You should have great success with that, if you're using TLS security, other wise not.  You probably have to get a Certificate that is more along the standard lines of what godaddy or tucows, not one you create yourself.

How is your squirrel mail client setup?  By that I mean, what type of connection settings are enabled?  And, can you connect to your server from anywhere as long as you use squirrel (send and receive)?

---

