---
title: "compiz &amp; compiz.real"
date: 2009-02-11
forum: General Help
---

### Post by Nisuspi on 2009-02-11
Newb question here, but should both compiz and compiz.real be running on my system simultaneously? AFAIK they're just different names for the same thing. 

Bit of back story, I'm running 8.10 which was upgraded from 8.04, and fear that a few driver reinstalls and playing around with windows decorators has left some trash behind in my startup scripts. My boot time from login screen to desktop takes ages, and generally people seem to think this is a compiz problem. Uninstalling & reinstalling compiz has helped, but I've just noticed both processes running and wonder if this is the root cause of my problem.

Output of ps ax | grep compiz is:

 8460 ?        S      0:00 /bin/sh /usr/bin/compiz
 8540 ?        SL     1:33 /usr/bin/compiz.real --ignore-desktop-hints --replace

---

