---
title: "Postfix wont start at startup"
date: 2012-10-23
forum: Desktop Environments
---

### Post by thomo2710 on 2012-10-23
Morning,

I am building a new Nagios monitoring machine.

Running 12.04 LTS Desktop 32-bit.

I have installed Postfix and mailx

But when my system starts up, the postfix service does not auto start and my machine refuses telnet connections and doesnt send any email.

I have to manually run service postfix start and then all is good until the next reboot.

I have looked at /etc/init.d and there is a postfix entry (in green) in there.

Can anybody help me please?

Thankyou

---

### Post by thomo2710 on 2012-10-23
Found the problem

My machine has multiple network cards.

IPv6 was causing the issue.

Adding this line to /etc/postfix/main.cf sorted it

inet_protocols = ipv4

---

