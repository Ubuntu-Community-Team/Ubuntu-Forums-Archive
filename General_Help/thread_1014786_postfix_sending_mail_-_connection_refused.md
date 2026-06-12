---
title: "postfix sending mail - connection refused"
date: 2008-12-18
forum: General Help
---

### Post by jspolen on 2008-12-18
Hi I'm trying to set up a mailserver at home, it works when trying to send in my own network but not any other mail.

I get the error:
[I]Dec 18 12:47:01 desktop-server postfix/pickup[18261]: D0F1B13A237: uid=1000 from=<server>
Dec 18 12:47:01 desktop-server postfix/cleanup[18307]: D0F1B13A237: message-id=<20081218114701.D0F1B13A237@desktop-server>
Dec 18 12:47:01 desktop-server postfix/qmgr[18263]: D0F1B13A237: from=<server@myownadress.com>, size=348, nrcpt=1 (queue active)
Dec 18 12:47:06 desktop-server postfix/smtp[18297]: connect to iris2.directnic.com[69.46.238.252]:25: Connection refused
Dec 18 12:47:06 desktop-server postfix/smtp[18297]: connect to iris1.directnic.com[69.46.238.251]:25: Connection refused
Dec 18 12:47:06 desktop-server postfix/smtp[18297]: D0F1B13A237: to=<someuser@soetast.com>, relay=none, delay=4.6, delays=0.08/0/4.5/0, dsn=4.4.1, status=deferred (connect to iris1.directnic.com[69.46.238.251]:25: Connection refused)
[/I]

This is my main.cf file
[I]# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = desktop-server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = myownadress.com, desktop-server, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
[/I]

---

