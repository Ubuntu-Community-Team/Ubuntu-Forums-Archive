---
title: "ssh: sftp: Name or service not known"
date: 2008-12-03
forum: General Help
---

### Post by jeffsa12 on 2008-12-03
I get the following error message when I try to sync me evo gmail pop, mail on my networked computers:

> ssh: sftp: Name or service not known

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]


The file paths are as follows:

/home/jeff/.evolution/mail/pop/jeffrs12@pop.gmail.com/cache

sftp://192.168.0.4/home/jeff/.evolution/mail/pop/jeffrs12@pop.gmail.com/cache

Is this going to work?

Is there a different way to do this?

---

### Post by deadowl on 2008-12-03
on whatever machines you're trying to talk to:

type in the console:
sudo apt-get install openSSH-server

---

### Post by jeffsa12 on 2008-12-03
Thanks deadowl,

Yea....I've already done that and can browse with Nautilus, files to and from the both computers.

---

