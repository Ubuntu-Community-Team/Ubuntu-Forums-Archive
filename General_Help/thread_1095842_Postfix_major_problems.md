---
title: "Postfix major problems"
date: 2009-03-14
forum: General Help
---

### Post by artheus on 2009-03-14
Hey!

I'm using Ubuntu Server edition 8.10 32-bit.

And I am having major problems with configuration of SMTP server with TLS-authentication in Postfix.

I will not be using postfix to anything other than a SMTP server.

Well.. I've tried to follow the instructions at
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")
but when I try to send mails with my Thunderbird mail-client in another computer in the network. And tries to send mail to a non-local recipient. I'll get the error message :
"Error accured. Mailserver answered 5.7.1 <account@mydomain.com>: Relay access denied."

My main.cf file :
```
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = servername
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = servername, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = ipv4
```

hope there are a simple solution for this!

Cheers,
Artheus

---

### Post by artheus on 2009-03-14
.................

---

### Post by artheus on 2009-03-14
Does anyone know how to fix this?

---

### Post by dcstar on 2009-03-15
> **artheus said:**
> Hey!

I'm using Ubuntu Server edition 8.10 32-bit.

And I am having major problems with configuration of SMTP server with TLS-authentication in Postfix.

I will not be using postfix to anything other than a SMTP server.

Well.. I've tried to follow the instructions at
[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")
but when I try to send mails with my Thunderbird mail-client in another computer in the network. And tries to send mail to a non-local recipient. I'll get the error message :
"Error accured. Mailserver answered 5.7.1 <account@mydomain.com>: Relay access denied."

My main.cf file :
```

.......
myhostname = servername
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = servername, localhost.localdomain, , localhost
relayhost = 
**mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128**
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
myorigin = /etc/mailname
inet_protocols = ipv4
```

hope there are a simple solution for this!

Cheers,
Artheus

The only "local" network you have specified is 127.0.0.0

And I do hope all those "servername" values are you changing things for this post, and not actually what is in that file.

---

### Post by artheus on 2009-03-15
Hey!
Yes! Those 'servername' values are me changing things for the post. Cause in the file it was the name of my server there, and that could as well be servername right?
So... What should I change 'mynetworks' to then? In the postfix tutorial it told me only to put 127.0.0.0. Should I set my ISP DNS IP?

Cheers

---

### Post by artheus on 2009-03-15
Well. Now I have configured the 'mynetworks' so it's correct.

And now my problem is.. When I try to send mail, the mail to a non-local user never get sent..
What can be wrong?

Should I change the communication ports?

Cheers

---

