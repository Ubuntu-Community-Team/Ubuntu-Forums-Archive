---
title: "Starting Spamd?"
date: 2005-02-14
forum: Desktop Environments
---

### Post by paul cooke on 2005-02-14
I'm trying to get spamassassin working in my personal mail chain the same way I had it going on Suse using this guide:

[http://www.tomchance.org.uk/research/random/kmail](http://www.tomchance.org.uk/research/random/kmail)

(how to get spamassassin going with Kmail)


I'm trying to startup the daemon spamd but keep getting this error even when launching using sudo:

paulc@big-box:~ $ spamd -m 2 -d -L
Could not create INET socket on 127.0.0.1:783: Permission denied (IO::Socket::INET: Permission denied)

the -m folowed by a number is the number of child processess. -d is telling it to daemonise itself and -L tells it to use local checks only (ie don't use reverse DNS checks with blacklists etc.)

I had no errors at all using this on Suse...


What am I not doing? I'm suspecting some permissions file somewhere where I've got to register port 783 as permitted. But I'm not sure what I should be doing.

Man spamd and reading the spamd readme don't give any help, neither does googling on the error message.

---

### Post by cblack on 2005-02-14
> paulc@big-box:~ $ spamd -m 2 -d -L

You weren't using sudo there. Do you get the permission denied error when really do use it?

---

### Post by paul cooke on 2005-02-15
[QUOTE=cblack]You weren't using sudo there. Do you get the permission denied error when really do use it?[/QUOTE]

read my post again... ;)

---

