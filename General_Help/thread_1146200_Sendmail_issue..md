---
title: "Sendmail issue."
date: 2009-05-02
forum: General Help
---

### Post by rapfnny on 2009-05-02
Ok, I recently had sendmail put on my server (Ubuntu 8.10 Server Edition) and it was working just fine. But after i restarted the server it stopped sending mail.
It is running.
```
root@bob-omb:/# ps axuww | grep sendmail                                                                                                      
root      4470  0.0  0.3   8752   836 ?        Ss   Feb25   3:15 sendmail: MTA: accepting connections          
root     19638  0.0  0.6   8744  1632 ?        Ss   11:28   0:00 sendmail -bd
root     19661  0.0  0.3   3236   784 pts/0    R+   11:28   0:00 grep sendmail
```

And when I try to send mail i get:
```
root@bob-omb:/# date | sendmail -v admin@bob-omb.net.   
admin@bob-omb.net.... Connecting to [127.0.0.1] via relay...
220 fnny.fnny.us ESMTP Sendmail 8.14.3/8.14.3/Debian-4; Sat, 2 May 2009 11:30:22 -0400; (No UCE/UBE) logging access from: bob-omb.net(OK)-smmsp@bob-omb.net [127.0.0.1]
>>> EHLO bob-omb.net
250-fnny.fnny.us Hello smmsp@bob-omb.net [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<root@bob-omb.net> SIZE=29 AUTH=root@bob-omb.net
250 2.1.0 <root@bob-omb.net>... Sender ok
>>> RCPT To:<admin@bob-omb.net>
>>> DATA
250 2.1.5 <admin@bob-omb.net>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
421 4.3.0 collect: Cannot write ./dfn42FUMY2019725 (bfcommit, uid=0, gid=119): No such file or directory
>>> QUIT
admin@bob-omb.net.... Deferred: 421 4.3.0 collect: Cannot write ./dfn42FUMY2019725 (bfcommit, uid=0, gid=119): No such file or directory
Closing connection to [127.0.0.1]   

```
When I check the logs, things similar to
> collect: Cannot write ./dfn42FUMY2019725 (bfcommit, uid=0, gid=119): No such file or directory
is what I always see.
I would appreciate any help to solve this issue. Thanks in advanced.

---

### Post by cmnorton on 2009-05-02
Is it possible something else happened before you restarted the server? 

Do you have enough disk space?

df

---

### Post by rapfnny on 2009-05-02
of course, i have plenty of space.

---

### Post by cmnorton on 2009-05-02
I cannot think of anything a restart would do to cause this.

It looks like the log you listed is of an interactive email session. It looks like there are insufficient privileges to write the temporary mail file. That looks like the email client's problem, not sendmail's.

---

### Post by pauna on 2009-05-03
> **rapfnny said:**
> 
And when I try to send mail i get:
[CODE]root@bob-omb:/# date | sendmail -v admin@bob-omb.net.   
admin@bob-omb.net.... Connecting to [127.0.0.1] via relay...
220 fnny.fnny.us ESMTP Sendmail 8.14.3/8.14.3/Debian-4; Sat, 2 May 2009 11:30:22 -0400; (No UCE/UBE) logging access from: bob-omb.net(OK)-smmsp@bob-omb.net [127.0.0.1]
>>> EHLO bob-omb.net
250-fnny.fnny.us Hello smmsp@bob-omb.net [127.0.0.1], pleased to meet you

I don't think the problem is in your box.

This looks like you tried to send mail to yourself via a RELAY machine fnny.fnny.us (unless that is an alias for your bob-omb.net?) and the error is from that relay machine. It probably has run out of disk space or something.

Then again, maybe your sendmail should not be configured to send e-mail to itself via a relay machine.

---

