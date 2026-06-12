---
title: "Send logs by mail with postfix"
date: 2006-05-28
forum: Desktop Environments
---

### Post by El_Matthews on 2006-05-28
Hello all,

I would like my system to send all logs etc by mail to my isp account.

So the first thing I did was to set up postfix, I choose the option satelite system (because no mail should be read localy), I hope this is correct ?

then I created an alias for root and for my normal account in the file /etc/aliases to
[email]account@isp.com[/email]. runned the command newaliases.

now when I test it with a :
telnet localhost 25
mail from: root
rcpt to: root
data
test
.
quit

i get in /var/log/mail.log 

May 28 10:22:20 srvubu postfix/master[7076]: daemon started -- version 2.2.4, configuration /etc/postfix
May 28 10:28:53 srvubu postfix/cleanup[8196]: DCAC442C380: message-id=<20060528082853.DCAC442C380@localhost.localdomain>
May 28 10:28:54 srvubu postfix/local[8198]: DCAC442C380: to=<fb517255@skynet.be>, orig_to=<root>, relay=local, delay=1, status=bounced (unknown user: "fb517255")
May 28 10:28:54 srvubu postfix/cleanup[8196]: 3FF4F42C381: message-id=<20060528082854.3FF4F42C381@localhost.localdomain>
May 28 10:28:54 srvubu postfix/local[8198]: 3FF4F42C381: to=<fb517255@skynet.be>, orig_to=<root@skynet.be>, relay=local, delay=0, status=bounced (unknown user: "fb517255")
May 28 10:52:59 srvubu postfix/smtpd[8223]: connect from srvubu[127.0.0.1]
May 28 10:53:12 srvubu postfix/smtpd[8223]: AADE442C37F: client=srvubu[127.0.0.1]
May 28 10:53:20 srvubu postfix/cleanup[8226]: AADE442C37F: message-id=<20060528085305.AADE442C37F@localhost.localdomain>
May 28 10:53:20 srvubu postfix/local[8227]: AADE442C37F: to=<fb517255@skynet.be>, orig_to=<mg>, relay=local, delay=15, status=bounced (unknown user: "fb517255")
May 28 10:53:20 srvubu postfix/cleanup[8226]: 5DADE42C381: message-id=<20060528085320.5DADE42C381@localhost.localdomain>
May 28 10:53:20 srvubu postfix/local[8227]: AADE442C37F: to=<fb517255@skynet.be>, orig_to=<mg>, relay=local, delay=15, status=bounced (unknown user: "fb517255")
May 28 10:53:20 srvubu postfix/cleanup[8226]: 5DADE42C381: message-id=<20060528085320.5DADE42C381@localhost.localdomain>
May 28 10:53:20 srvubu postfix/local[8227]: 5DADE42C381: to=<fb517255@skynet.be>, orig_to=<root@skynet.be>, relay=local, delay=0, status=bounced (unknown user: "fb517255")
May 28 10:53:21 srvubu postfix/smtpd[8223]: disconnect from srvubu[127.0.0.1]


Why isn't it delivered to my isp mail (fb517255@skynet.be). I don't understand what I am doing wrong. Can sombody help me ?

After the mail delivery is correct, how do I set up Ubuntu to send logs by mail ?

Thanks

---

### Post by El_Matthews on 2006-05-29
Nobody has any idea how I could proceed to troublehsoot this problem ?

---

### Post by hw-tph on 2006-05-29
While I'm not 100% sure of it, I don't think you can have an alias pointing to an account on another server. However, you should be able to use a .forward file to forward mail that comes into your account to the account of your choice (like on your ISP).

Type **man 5 master** for more info.

---

### Post by El_Matthews on 2006-06-01
Sorry for the late reply but I didn't had much time to test this out.

I created a forward file in my profille, set the permission to 0640. now in the mail log I receive a status delivered but I didn't receive anything in my mailbox.

Is there a way to test my postfix setup while bypassing alliases etc. sent a mail using my postfix config from my ISP account to an other ?

---

### Post by El_Matthews on 2006-06-13
gents

it seems that my config is correct but postfix remaps the send to to undisclosed recipients when configured as sateliet system, I suppose that this isn't accepted by my provider. last possibility is also that the send from isn't accepted.

Anybody an idea how I can bypass providor security settings? 

greetings 

Matthieu

---

### Post by cstudent on 2006-06-13
I use log2mail to send specific log entries to me by email. It's in the repos. You can find out a little bit more at:

[http://people.debian.org/~enrico/log2mail/](http://people.debian.org/~enrico/log2mail/)

.

---

