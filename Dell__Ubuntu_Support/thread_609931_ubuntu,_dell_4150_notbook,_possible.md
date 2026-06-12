---
title: "ubuntu, dell 4150 notbook, possible?"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by scripteaze on 2007-11-11
cant seem to get ubuntu 7.10 installed on dell 4150 notebook..anyony do this yet with this version?

Thank you

errors:

buffer i/o error on fd0: error at block 0

the error was similar to that, but not word for word.I did disable all onboard fd controlers, also pulled the batery out..thank you guys in advance:confused:

---

### Post by scripteaze on 2008-02-11
Well, i guess im posting help for my own question. It seems as though i am the only person on earth that had issues installing ubuntu on a dell 4150 laptop. Anyways.

here is my fix, maybe it will help someone else.

(1):KS
install ubuntu server 7.10, not desktop edition

(2):KS
when finished, it will hang on something, i forget, just hit enter and you should be dropped at the prompt

(3):KS
from ssh, after logging in, type:
sudo apt-get install ubuntu-desktop
============================

Thats pretty much it..

if you have any issues, hit me up at scripteaze[at]g.m.a.i.l

---

