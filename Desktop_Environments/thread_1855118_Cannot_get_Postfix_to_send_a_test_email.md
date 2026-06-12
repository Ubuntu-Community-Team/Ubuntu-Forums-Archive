---
title: "Cannot get Postfix to send a test email"
date: 2011-10-05
forum: Desktop Environments
---

### Post by rbowen1 on 2011-10-05
Running 10.04 LTS 32 bit desktop.  Installed Postfix but cannot get it to send a test email.  I want to use Postfix as a Gmail SMTP relay for a camera security system that I have running on the unit.    I use the "sendmail" command in terminal and the cursor moves down one line and stays in the far left.   Appears frozen,  I have to close the terminal window and open a new one.   I never see any errors or events in mail.log.    If i do a "postfix reload" I can see where postfix reloads in the mail.log.   I have checked all the logs in var/log and no errors are being produced.   

Here is the /etc/postfix/main.cf
relayhost = smtp.gmail.com:587
mydomain = local.domain
myhostname = host.local.domain
myorigin = $myhostname
smtpd_sasl_path = smtpd
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_type = cyrus
smtp_sasl_auth_enable = yes
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_use_tls  = yes
smtp_tls_CAfile = /usr/share/ncat/ca-bundle.crt
smtp_sasl_tls_security_options = noanonymous

any ideas on where else I can look?   All help will be appreciated.

---

### Post by rbowen1 on 2011-12-19
Going to solve out this thread.  Went to evolution email client.:popcorn:
Ubuntu Rocks!

---

### Post by lisati on 2011-12-19
It sounds like the sendmail command is waiting for input.

---

