---
title: "Amavis, Postfix, ClamD, Spamassassin Email server error"
date: 2009-03-01
forum: General Help
---

### Post by mlbarnes on 2009-03-01
I am using Ubuntu 8.10

I have a Amavis, Postfix, ClamD, Spamassassin Email server. I used this HOWTO to setup my server: [http://chiralsoftware.com/linux-system-administration/ubuntu-postfix-imap-dovecot-setup.seam;jsessionid=D0A51C05C9B09543B869A54ED2550E87](http://chiralsoftware.com/linux-system-administration/ubuntu-postfix-imap-dovecot-setup.seam;jsessionid=D0A51C05C9B09543B869A54ED2550E87)

The errors I am getting are:

1. postfix/trivial-rewrite[26392]: warning: do not list domain example.com in BOTH mydestination and virtual_alias_domains

2.
(16131-10) (!!)run_av (ClamAV-clamd) FAILED - unexpected , output="/var/lib/amavis/tmp/amavis-20090301T100257-16131/parts: lstat() failed. ERROR\n"

(16131-10) (!!)ClamAV-clamd av-scanner FAILED: CODE(0xa33b088) unexpected , output="/var/lib/amavis/tmp/amavis-20090301T100257-16131/parts: lstat() failed. ERROR\n" at (eval 98) line 527.

(16131-10) (!!)WARN: all primary virus scanners failed, considering backups


I would appreciate any help you can give me. I have been searching the internet to find an answer and have had no luck.

main.cf:

#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
minimal_backoff_time = 300s
maximal_backoff_time = 1200s
maximal_queue_lifetime = 1d
bounce_queue_lifetime = 1d
smtp_helo_timeout = 60s
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12
append_dot_mydomain = no
readme_directory = no
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_tls_loglevel = 1
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,
                               permit_mynetworks,
                               reject_unauth_destination
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sasl_path = /var/spool/postfix/private/dovecot-sasl-auth
inet_interfaces = all
inet_protocols = ipv4
myhostname = cora.example.com
mydomain = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
relayhost =
mynetworks =
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mydestination = $myhostname, /etc/postfix/virtual/domains
virtual_maps  = hash:/etc/postfix/virtual/addresses

addresses:
example.com                      DOMAIN
[email]barnes@example.com[/email]               barnes
[email]support@example.com[/email]              barnes

domains:
example.com
example.net



If you need any other files posted please let me know. I am pretty sure the main.cf is where the errors are coming from.

---

