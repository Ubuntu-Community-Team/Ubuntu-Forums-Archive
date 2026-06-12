---
title: "No POP in Kontact over 3G?"
date: 2007-06-21
forum: Desktop Environments
---

### Post by Hospitaller on 2007-06-21
I just got a Huawei E220 3G-modem for my laptop running Kubuntu, and it works really great apart from one thing - I can't retrieve my mail messages from my mail server in Kontact/Kmail. I can send mail, no problem, but I can't fetch my incoming mails.

This has never been any problem, when I used WLAN or wired access, so there aren't any problems with the POP account in Kontact. I can also do a 'telnet my.mailserver.se 110' and get a connection to the mailserver so I can definately reach the server over the ppp-connection but if I run Wireshark and listens on the ppp0 interface and then press button to fetch mail in Kontact there is absolutely no traffic whatsoever. It is as if the POP-component in Kontact doesn't realise that I have a connection. Really strange, especially since the SMTP account in Kontact works fine.

Has anyone seen something like this before?

---

