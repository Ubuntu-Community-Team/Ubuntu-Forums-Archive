---
title: "can't connect via ssh or connect to gaim apps"
date: 2005-10-23
forum: Desktop Environments
---

### Post by sickOfWindows on 2005-10-23
newb here with fresh install of 5.10.  at first i couldn't browse url's, and changing 'network.dns.disableIPV6' value to True fixed that, but still cannot ssh into my school's server, connect to gaim applications, or send mail through evolution - i'm hoping these problems are all related so one tweak fixes them all, but have no idea.  any tips to fix this or pointers to where this is posted are appreciated.  thanks.

---

### Post by LorenzoD on 2005-10-23
Are you perhaps behind a firewall/router/proxy/whatever that doesn't allow these types of traffic through (SSH, SMTP, Yahoo, Jabber etc)?

---

### Post by HermanAB on 2005-10-23
This sounds like a general connectivity problem.

Open a terminal and run some tests to narrow things down:

$ /sbin/ifconfig
Check whether your general IP settings are OK.

$ ping [www.yahoo.com](www.yahoo.com)
If that doesn't work, then your DNS is like wrong.

$ cat /etc/resolv.conf
See whether the DNS addresses make sense and try to ping them.

$ ping your.mail.server
If that doesn't work, then Evolution won't be able to fetch mail

$ telnet your.mail.server  110
If that doesn't respond then POP won't work.

$ telnet your.mail.server 25
If that doesn't work then SMTP won't work and Evolution won't be able to send mail.

See this guide for some more mail debug tips - somewhere in the middle:
[http://www.aerospacesoftware.com/fubar-howto.html](http://www.aerospacesoftware.com/fubar-howto.html)

Cheers,

Herman

---

### Post by sickOfWindows on 2005-10-23
negative.  i'm behind a router, but (don't tell anyone) the firewall is disabled, and i can ssh using putty on windows and connect to all other im programs with windows on the same network.  sorry for not clarifying that.

---

### Post by sickOfWindows on 2005-10-23
thanks Herman.  will run those tests later - must go to the lab to write stupid Haskell scripts (god i hate that language)  cheers to you too ;)

---

