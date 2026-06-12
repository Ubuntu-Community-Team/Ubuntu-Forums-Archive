---
title: "Small Postfix problem -- any suggestions?"
date: 2008-12-03
forum: General Help
---

### Post by fooey on 2008-12-03
followed
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts-p5")

----

all works - _i can send & receive e-mails JUST FINE_, but i can't see incoming mails with Squirrelmail nor using evolution/outlook on other computers. 
i can read incoming mails fine on the server itself via **cmd** line ...just not from another computer using squirrel mail/outlook/evolution.
sending mails from any of those mail clients above works like it should & the sent mails go in their proper folder. just nothing is in my "Inbox" section of those mail clients.

Any ideas?
(i'm using courier-imap)

everything goes in my users Mailbox dir in their home dir... like it should. 
i just can't figure out why sm or outlook aren't grabbing mail that has been received.

need more info let me know. THANKS
(I'm assuming this should be a fairly easy fix since i can receive mail just fine??)
----------
if anyone does reply i'm sure you'll wana see my main.cf:

```

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_vrfy_command = yes
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$extension"
mailbox_size_limit = 0
maximal_backoff_time = 8000s
minimal_backoff_time = 1000s
mydestination = <mydomain.com>, saturn, localhost.localdomain, localhost, 192.168.1.0/24
myhostname = saturn
mynetworks = 127.0.0.0/8 192.0.0.0/8 <myipIShere>/32
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = [mail.charter.net]
smtp_helo_timeout = 60s
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/charter/sasl_passwd
smtp_sasl_security_options = 
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynew.nl, reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12
smtpd_helo_required = yes
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_unauth_pipelining, permit_mynetworks, reject_unauth_destination, reject_rbl_client zen.spamhaus.org
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_sender_restrictions = check_sender_access hash:/etc/postfix/access, reject_unknown_sender_domain, permit_mynetworks, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom

```

---

### Post by fooey on 2008-12-04
anyone?:confused:

---

### Post by fooey on 2008-12-04
well crap. i was really thinking this was just a QUICK fix

---

### Post by Phases on 2008-12-04
I've posted a few squirrelmail threads and posted on a few exsisting threads for help and haven't got responses either. 

My guess is it's such a complex process (mine anyway.. I followed half of flurdy's guide) that no one wants to jump into what will probably turn into a long process of troubleshooting with us.

At least you got this far though.. I can't even log in! 

Good luck.

---

