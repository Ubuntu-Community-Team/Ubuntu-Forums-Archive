---
title: "D620 - Hardy - Slow Wireless connection"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by walterhtx on 2008-06-30
Ubuntu 8.04
Latitude D620
Dell Wireless 1490 dual band (a/b/g)

When running XP or Vista it connects at 54Mbps reliably. When running Ubuntu I get a maximum connection of 2Mbps and the connection is flaky, at best(this also occurred in previous releases of Ubuntu).

Anyone else experiencing extremely slow wireless connectivity with this adapter? Is it something that I'm doing wrong, or something I just haven't done? Any help will be much appreciated! :confused:

---

### Post by backwardselvis on 2008-07-27
Yup, I also am experiencing a very flaky/slow connection.

---

### Post by Ru$$i@N on 2008-07-28
same here.
i'm running hardy but on a different laptop. i've noticed that my rate on the wireless droppes to 1 or 2M. i added pre-up line to /etc/network/interfaces, but that didn't help.

---

### Post by Ru$$i@N on 2008-07-28
same here.
i'm running hardy but on a different laptop. i've noticed that my rate on the wireless droppes to 1 or 2M. i added pre-up line to /etc/network/interfaces, but that didn't help.

---

### Post by maracambus on 2008-07-28
Hi there!

I have same problem with Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05) card. It is slow passing traffic though even local network. I was trying to stream video file from Windows share and max speed was 900kbit and it reached it only ones. Network traffic graphs wile streaming look more like a human cardio: /\_/\___/\___.
Same 8.04 version of Ubuntu.

Any suggestions are welcome.

---

### Post by ARhere on 2008-10-23
Fix available here.

[http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html](http://www.overclock.net/linux-unix/368589-solved-slow-wireless-speeds-ubuntu-but.html)

I have not applied it yet to my mini-9 so let me know how well it works for everyone.

-AR

---

