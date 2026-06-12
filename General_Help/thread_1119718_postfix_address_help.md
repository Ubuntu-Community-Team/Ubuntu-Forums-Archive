---
title: "postfix address help"
date: 2009-04-08
forum: General Help
---

### Post by Wonslung on 2009-04-08
hey guys, i finially got postfix up and running....i'm able to send and recieve mail but the problem is i need it to rewrite the "from" address

example...i send out mail and it'll be from [email]wonslung@foo.local[/email]

i need it to be from [email]wonslung@example.org[/email]

how do i do this?

---

### Post by Wonslung on 2009-04-08
i figured this out incase anyone else needs to know
in main.cf (/etc/postfix/main.cf) add a line that says
smtp_generic_maps = hash:/etc/postfix/generic


then save

then create /etc/postfix/generic with your editor

[email]wonslung@foo.local[/email]        [email]wonslung@example.com[/email]
[email]jeff@foo.local[/email]            [email]jeff@example.com[/email]


then save it
restart postfix

---

### Post by Wonslung on 2009-04-08
ok...now i have another problem....i send and receive mail fine from within webmin using the postfix module but i want to be able to use an email program like thunderbird on a seperate machine on the same network....i can't figure out how to set it up....i put the network address under my networks in the main.cf but no settings i use in thunderbird seem to work
```
  GNU nano 2.0.7                                                     File: /etc/postfix/main.cf                                                                                                                

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
masquerade_domains = wonslung-raid.local wonslung.no-ip.org
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

myhostname = wonslung-raid.local
smtp_generic_maps = hash:/etc/postfix/generic
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = wonslung.no-ip.org, wonslung-raid.local, localhost.local, localhost
relayhost =
mynetworks = 127.0.0.0/8 192.168.1.1/24 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


```

that is my main.cf....any help would be appreciated

sheesh, i figured this out too by looking at the logs.....the problem was that 192.168.1.1/24 should have been 192.168.1.0/24

---

