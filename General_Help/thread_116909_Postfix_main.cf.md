---
title: "Postfix main.cf"
date: 2006-01-13
forum: General Help
---

### Post by trawler on 2006-01-13
I've been trying to set up a mail server according to [this]("http://flurdy.com/docs/postfix/") howto. 

The problem is, that about half way through the guide i found out my server isn't responding to telnet requests.
It shows that it's connected, but i'm not getting the usual response (220 localhost.localdomain ESMTP Postfix) (localhost.localdomain replaced by domain name of course).

I've tried messing around with the main.cf file, but i haven't been able to pin-point the problem - sometimes i could get a telnet response, but most of the time i can't.

eventually i replaced the main.cf file with the one created after initial installation (i kept the original) and now it seems to be responding well to telnet again - so i figure - something must be wrong with the main.cf, but i don't know why...

i'm attaching the following files - the current main.cf and the original install one - hope someone out there could let me know what's wrong with it?

---

### Post by dcstar on 2006-01-13
[QUOTE=trawler]I've been trying to set up a mail server according to [this]("http://flurdy.com/docs/postfix/") howto. 

The problem is, that about half way through the guide i found out my server isn't responding to telnet requests.
It shows that it's connected, but i'm not getting the usual response (220 localhost.localdomain ESMTP Postfix) (localhost.localdomain replaced by domain name of course).

I've tried messing around with the main.cf file, but i haven't been able to pin-point the problem - sometimes i could get a telnet response, but most of the time i can't.

eventually i replaced the main.cf file with the one created after initial installation (i kept the original) and now it seems to be responding well to telnet again - so i figure - something must be wrong with the main.cf, but i don't know why...

i'm attaching the following files - the current main.cf and the original install one - hope someone out there could let me know what's wrong with it?[/QUOTE]
If you type in "sudo postfix restart" (in a user terminal), what is the result?

---

### Post by trawler on 2006-01-13
[QUOTE=dcstar]If you type in "sudo postfix restart" (in a user terminal), what is the result?[/QUOTE]

i got this:
postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)

maybe you mean reload? cause i tried it already. also did stop and start to make sure and still same result

---

### Post by dcstar on 2006-01-13
[QUOTE=trawler]i got this:
postfix/postfix-script: fatal: usage: postfix start (or stop, reload, abort, flush, check, set-permissions, upgrade-configuration)

maybe you mean reload? cause i tried it already. also did stop and start to make sure and still same result[/QUOTE]
Yes, my error.

What happens when you type:

telnet localhost 25

---

### Post by trawler on 2006-01-13
[QUOTE=dcstar]Yes, my error.

What happens when you type:

telnet localhost 25[/QUOTE]

same result:
```
user@ubuntu:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
```

and it stays like that... unless i revert to the original config, then i get:
```
user@ubuntu:~$ telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
220 localhost.localdomain ESMTP Postfix (Ubuntu)

```

---

### Post by trawler on 2006-01-14
*bump*

Any One?
I've been wracking my brain on this one for hours... I've even tried completely different tuturials - but so far with no success...

---

### Post by trawler on 2006-01-14
Finally!

I've been messing around with this problem for 2 days and after EXTENSIVE debugging i've been able to figure out that the problem was the mysql mappings at the end of the file...

An hour later i found i didn't have the postfix-mysql installed... ](*,) 
Installing the package solved my problem, of course. \\:D/

---

