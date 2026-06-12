---
title: "Postfix not collecting external email"
date: 2008-12-06
forum: General Help
---

### Post by christiebunny on 2008-12-06
I just installed dovecot, and postfix as per:  [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

It worked fine briefly but this morning when I woke up, postfix was broke, wouldn't start.

I think I've got everything reinstalled and cleaned up, but i'm still not getting external mail. Or internal for that matter. I tried telnetting into port 25 from localhost, and send a mail manually -- but it gives me "451 4.3.0 Temporary system failure. Please try again later."

As far as I know, everything in the config files are identical to whats in the above link, with the exception of 'mydestination' and 'myhostname'.

Yet, any mail sent to that server just seems to vanish-- I'm not getting bouncebacks (yet), or any other error on the sending side, it just vanishes.

Anyone have any idea what might be wrong?



<edit> I did notice this when I telnetted in to port 25:
ehlo localhost
250-cutiebunny.gateway.2wire.net Hello localhost [127.0.0.1], pleased to meet you
250 ENHANCEDSTATUSCODES


I know there should be more then that, but i'm not sure how to add anything else in to that list.

---

### Post by albinootje on 2008-12-06
First, try : mailq
And see what that gives as a possible answer.
Then look at the logfiles.
For example : tail -f /var/log/syslog
(Or tail -f /var/log/syslog.0)
Could be lack of disk-space or lack of resources (RAM).

---

### Post by christiebunny on 2008-12-06
> **albinootje said:**
> First, try : mailq
And see what that gives as a possible answer.
Then look at the logfiles.
For example : tail -f /var/log/syslog
(Or tail -f /var/log/syslog.0)
Could be lack of disk-space or lack of resources (RAM).

mailq gives me: 

postqueue: fatal: Queue report unavailable - mail system is down

and "tail -f /var/log/syslog" gives:


Dec  6 19:19:21 cutiebunny sm-mta[13125]: mB72JLu5013099: SYSERR(root): hash map "access": missing map file /etc/mail/access.db: No such file or directory
Dec  6 19:19:22 cutiebunny sm-mta[13125]: mB72JLu5013099: ruleset=tls_rcpt, arg1=benloc@sipnsearch.com, relay=smtp-in-2.userservices.net., reject=451 4.3.0 Temporary system failure. Please try again later.
Dec  6 19:19:22 cutiebunny sm-mta[13125]: mB72JLu5013099: to=benloc@sipnsearch.com, delay=00:56:51, xdelay=00:00:01, mailer=esmtp, pri=570000, relay=smtp-in-2.userservices.net. [204.16.46.1], dsn=4.5.0, stat=Operating system error
Dec  6 19:19:23 cutiebunny sm-mta[13125]: mB6M9nPA010986: to=christie@bunny.thewarren.ws, delay=05:08:44, xdelay=00:00:01, mailer=esmtp, pri=2910012, relay=cutiebunny.gotdns.com. [75.172.52.247], dsn=4.0.0, stat=Deferred: Connection refused by cutiebunny.gotdns.com.
Dec  6 19:21:41 cutiebunny postfix/postqueue[13145]: fatal: Queue report unavailable - mail system is down


it says connection refused, but I know port 25, and port 110, are open...  ah well, at least this mess'll teach me something, whatever's wrong! :)

---

### Post by dcstar on 2008-12-07
> **christiebunny said:**
> I just installed dovecot, and postfix as per:  [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

It worked fine briefly but this morning when I woke up, postfix was broke, wouldn't start.

I think I've got everything reinstalled and cleaned up, but i'm still not getting external mail. Or internal for that matter. I tried telnetting into port 25 from localhost, and send a mail manually -- but it gives me "451 4.3.0 Temporary system failure. Please try again later."
.........

```
sudo dpkg-reconfigure postfix
```

and select "Internet Site"

---

### Post by christiebunny on 2008-12-07
> **dcstar said:**
> ```
sudo dpkg-reconfigure postfix
```

and select "Internet Site"

Done, but it still says mail system is down-- and tail /var/log/syslog  gives:

Dec  6 21:26:18 cutiebunny postfix/master[13482]: fatal: bind 0.0.0.0 port 25: Address already in use
Dec  6 21:26:23 cutiebunny postfix/postqueue[13486]: fatal: Queue report unavailable - mail system is down

---

### Post by dcstar on 2008-12-07
> **christiebunny said:**
> Done, but it still says mail system is down-- and tail /var/log/syslog  gives:

Dec  6 21:26:18 cutiebunny postfix/master[13482]: fatal: bind 0.0.0.0 **port 25: Address already in use**
Dec  6 21:26:23 cutiebunny postfix/postqueue[13486]: fatal: Queue report unavailable - mail system is down

Then you have another MTA installed that prevents postfix from starting.

---

### Post by christiebunny on 2008-12-07
> **dcstar said:**
> Then you have another MTA installed that prevents postfix from starting.

I uninstalled postfix, and dovecot, an deleted the /etc/dovecot and /etc/postfix dirs, trying to start over-- however, port 25 is still open. Telnetting to there, I get:

```
220 cutiebunny.gateway.2wire.net ESMTP Sendmail 8.14.1/8.14.1/Debian-8ubuntu1; Sun, 7 Dec 2008 10:59:07 -0800; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
```

I tried to uninstall sendmail and esmtp, but neither are installed according to apt. But I'm done playing with it until I can figure out how to get that port turned off and everything cleaned up... then I'll try again from scratch.  I hope its soon tho, I'm losing mail *sigh*


p.s. and I feel dumb -- port 25 *incoming* is closed-- I was telnetting to the outgoing port 25, which is open... still a problem I think, but I should probably make it clear _which_ port 25 I meant....

---

### Post by christiebunny on 2008-12-09
Anyone have any ideas?

---

### Post by n3hima on 2009-05-21
Hi, you still having problems with this?
A google search brought me here (I was having the exact same problem)...

It looks like this happens when you uninstall sendmail and install postfix: the actual sendmail process doesn't terminate and is still glommed onto port 25. I used a "sudo killall sendmail" to get rid of it, and then restarted postfix and it all worked. If you already uninstalled sendmail using aptitude you may want/need to manually delete the /usr/sbin/sendmail executable, but it won't be run on startup even if you don't delete it as the uninstall script removes the entry from /etc/init.d/

HTH

Joe

---

