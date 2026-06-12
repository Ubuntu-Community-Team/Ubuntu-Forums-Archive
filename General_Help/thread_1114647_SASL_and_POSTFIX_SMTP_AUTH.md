---
title: "SASL and POSTFIX SMTP AUTH"
date: 2009-04-03
forum: General Help
---

### Post by Adabard on 2009-04-03
For some reason my username and password is not working in the way that it is supposed to. It works when using the testsaslauthd username, but it doesn't when generating the encrypted version. 

root@adabard:/etc/postfix# testsaslauthd -u test -p testpass
0: OK "Success."

It doesn't work here though:

root@adabard:/etc/postfix# perl -MMIME::Base64 -e 'print encode_base64("test\0test\0testpass");'
dGVzdAB0ZXN0AHRlc3RwYXNz
root@adabard:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ltdev.org ESMTP Postfix (Ubuntu)
ehlo localhost
250-ltdev.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH NTLM PLAIN DIGEST-MD5 LOGIN CRAM-MD5
250-AUTH=NTLM PLAIN DIGEST-MD5 LOGIN CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN dGVzdAB0ZXN0AHRlc3RwYXNz
535 5.7.8 Error: authentication failed: authentication failure

---

### Post by hyper_ch on 2009-04-03
I'd follow the perfect howtos by falko on [http://www.howtoforge.com](http://www.howtoforge.com) --> those work.

---

### Post by Adabard on 2009-04-03
This is my /etc/postfix/main.cf file:
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtp_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ltdev.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ltdev.org, adabard.Belkin, localhost.Belkin, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = sasl/smtpd
stmp_sasl_type = cyrus
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks check_relay_domains check_relay_domains
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom



This is my /etc/postfix/sasl/smtpd.conf:
pwcheck_method: saslauthd
mech_list: PLAIN LOGIN


I have /etc/default/saslauthd specified to:
MECHANISMS="shadow"

All the processes are obviously running...I just can't authenticate.

---

### Post by Adabard on 2009-04-03
I just found this in the /var/log/mail.log file
Apr  3 08:02:43 adabard postfix/smtpd[24669]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Apr  3 08:02:43 adabard postfix/smtpd[24669]: warning: SASL authentication failure: Password verification failed
Apr  3 08:02:43 adabard postfix/smtpd[24669]: warning: localhost[127.0.0.1]: SASL PLAIN authentication failed: generic failure

---

### Post by Adabard on 2009-04-03
Fixed it, it was a permissions issue. Postfix wasn't in the group sasl... *head desk*

---

### Post by Ovis on 2011-02-07
> **Adabard said:**
> For some reason my username and password is not working in the way that it is supposed to. It works when using the testsaslauthd username, but it doesn't when generating the encrypted version. 

root@adabard:/etc/postfix# testsaslauthd -u test -p testpass
0: OK "Success."

It doesn't work here though:

root@adabard:/etc/postfix# perl -MMIME::Base64 -e 'print encode_base64("test\0test\0testpass");'
dGVzdAB0ZXN0AHRlc3RwYXNz
root@adabard:/etc/postfix# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 ltdev.org ESMTP Postfix (Ubuntu)
ehlo localhost
250-ltdev.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH NTLM PLAIN DIGEST-MD5 LOGIN CRAM-MD5
250-AUTH=NTLM PLAIN DIGEST-MD5 LOGIN CRAM-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN dGVzdAB0ZXN0AHRlc3RwYXNz
535 5.7.8 Error: authentication failed: authentication failure

main.cf:
          #smtpd_sasl_path = 
          broken_sasl_auth_clients = yes
          smtpd_sasl_type = cyrus
          cyrus_sasl_config_path = /etc/postfix/sasl

and
master.cf:
#
smtp      inet  n       -       n       -       -       smtpd
#
---------------------
and your troubles should be resolved

---

