---
title: "mutt setup problem"
date: 2007-07-23
forum: Desktop Environments
---

### Post by rliston on 2007-07-23
Hi all,

I would like to usemutt on my desktop. I'm using 6.06 LTS in an exchange server environment using IMAP. I've done a good bit of reading about mutt setup but am now rather confused about to proceed. Any assistance with the correct incantation would be much appreciated.

Some background:

I was using 5.10 (breezy) and had mutt set up properly, although I don't remember exactly how I got it set up. I know I was using IMAP with our local exchange server. My attempted upgrade to 6.06 LTS did not go well, so I had to do a fresh install. I tried to set up Evolution (because last time I did this I vaguely remember that it helped), then reinstated my .muttrc. I was then able to connect and receive email with mutt via IMAP from the server, but my sent mail either gets queued to /var/mail/username or goes into a black hole (never received my test mails, nor can I find them queued anywhere).

Some questions:

Should I be using postfix for sending mail? (I think I was using sendmail before, but it looks like postfix is now recommended.) If I should use postfix, do I need to go through all the steps listed at this site? 

[https://help.ubuntu.com/community/Postfix#head-03aabdc63308fc3cc400f134e190dca759dd2bc6](https://help.ubuntu.com/community/Postfix#head-03aabdc63308fc3cc400f134e190dca759dd2bc6)

I'm pretty sure I didn't have to do all of this before.

I'll fill in the blanks as needed. Suggestions much appreciated. 

Richard

---

### Post by rliston on 2007-07-24
Still struggling with mutt/postfix... more info:

I just tried to send email to myself and this is the (modified) result in /var/log/mail.log:

Jul 24 09:58:20 localhost postfix/pickup[5101]: 1FA6467F55: uid=1000 from=<rliston>
Jul 24 09:58:20 localhost postfix/cleanup[5377]: 1FA6467F55: message-id=<20070724135820.GA5365@mymachine.mydomain.org>
Jul 24 09:58:20 localhost postfix/qmgr[5102]: 1FA6467F55: from=<rliston@mydomain.org>, size=649, nrcpt=1 (queue active)
Jul 24 09:58:20 localhost postfix/smtp[5379]: 1FA6467F55: to=<rliston@mydomain.org>, relay=mailsrvr.mydomain.org[198.17.40.7], delay=0, status=sent (250 2.0.0l6O7tEmg058452 Message accepted for delivery)
Jul 24 09:58:20 localhost postfix/qmgr[5102]: 1FA6467F55: removed

I would have expected "Message accepted for delivery" to indicate success, but nothing appeared in my inbox.

Any thoughts?

Richard

---

### Post by andrew.46 on 2007-07-25
Hi,

 Saw your post:

> **rliston said:**
> Hi all,

I would like to usemutt on my desktop. I'm using 6.06 LTS in an exchange server environment using IMAP. I've done a good bit of reading about mutt setup but am now rather confused about to proceed. Any assistance with the correct incantation would be much appreciated. [...]

 I am a big fan of mutt and have recently published a page that deals with setting it up under Ubuntu:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 This page is aimed towards Mutt and Gmail so you would need to alter more than a few things, in particular it does not cover IMAP. Perhaps this may help:

[http://mutt.sourceforge.net/imap/](http://mutt.sourceforge.net/imap/)

 I hope you glean enough from these 2 sources to get yourself up and running!

                Andrew

---

### Post by nigeldgreen on 2007-07-25
I used to use postfix with Mutt but last time I set it up I got tripped up with all the settings and never really felt that I had it working right.  I'm now using fetchmail/procmail to retrieve and file my messages, mutt for message viewing and esmtp to send mail.

I couldn;t just remove postfix as mutt has dependencies on it, to remove it and install esmtp I had to go through this process:
[LIST]
[*]Do "sudo aptitude remove postfix" in a terminal - it will spot the dependency on postfix for Mutt and offer to fix things.
[*]Select 'n' to the options until it gives you the option to install esmtp.
[*]Select 'y' and it will install esmtp and remove postfix.
[/LIST]

You will need to create an ~/.esmtprc file - the manpage is online at: [http://esmtp.sourceforge.net/esmtprc.5.html](http://esmtp.sourceforge.net/esmtprc.5.html)

It all worked great for me, but your mileage may vary.

Nigel

---

### Post by rliston on 2007-07-25
Ok, thanks for the responses, folks.

I'm not saying it's the best way to do it, but here's what eventually worked for me... the fix echoes [http://lists.debian.org/debian-user/2007/07/msg00028.html](http://lists.debian.org/debian-user/2007/07/msg00028.html)

I kept thinking my setup was close, so I continued searching and massaging my config. I wanted to use mutt/linux/postfix in our Exchange environment, but I discovered that I couldn't send mail with "telnet our.server 25", but at least it told me what AUTH methods were available. I could then successfully do an "AUTH LOGIN" via telnet (with much googling going on in the meantime). I finally figured out that I needed to setup my postfix main.cf so that:

1) it actually points to the correct one of our mail servers

relayhost = [the.correct.server]
(btw, our MX record is incorrect for internal mail --- not a battle I'm going to fight, though)

2) it does auth login:

smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = login
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd

and 3) the /etc/postfix/sasl_passwd is populated and permissions set up. Helpful here were:

[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/index.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/index.html)
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_process.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_process.html)
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html)
(Had to install metamail, then use "mimencode")
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html)
[http://www.computerperformance.co.uk/exchange2003/exchange2003_SMTP_Auth_Login.htm](http://www.computerperformance.co.uk/exchange2003/exchange2003_SMTP_Auth_Login.htm)
[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)

Anyway, I seem to be up and running now!

Cheers,
Richard

---

