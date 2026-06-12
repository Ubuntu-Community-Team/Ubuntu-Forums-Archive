---
title: "no mail to my postfix systems...."
date: 2006-03-06
forum: Desktop Environments
---

### Post by kline on 2006-03-06
Hopefully, some Postfix wizard can help me get mail going from my DNS server
which is running sendmail to my Ubuntu systems.  Somehow, last summer I had mail working bi-directionallly.  It would get out and back into [email]kline@ethic.thought.org[/email].
This was with 5.04.  

I edited main.cf and master.cf and it was automagic.  Now, nothing.

Anybody?

thanks much,

gary kline

---

### Post by kline on 2006-03-06
Well,  it wasn't the fault of Postfix; nothing on my test server wsas amiss.
The last time I rebooted my DNS servem DHCP decided to toss out a new IP.
With the old IP iin /etc/hosts, sendmail gave an auto-deny....  Relaying all mail was ferboten.    My fault.

gary
PS:   yes, i am mking notes.  :-|

---

