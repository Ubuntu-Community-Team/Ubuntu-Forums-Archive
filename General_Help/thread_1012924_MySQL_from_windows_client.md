---
title: "MySQL from windows client"
date: 2008-12-16
forum: General Help
---

### Post by Stunts on 2008-12-16
Hi all. Sorry if this is the wrong place to post, but it seemed adequate.
I have a computer running Hardy and a MySQL server. I can connect remotely from several computers including from VPN, but they all run linux. Today I needed to access the database from a windows client on the same network and I had no luck.
From the CLI running 
```
mysql -u user -p -h 10.101.134.40
```prompts for my password and then just sits there idle. No error msg, no nothing.
I have also tired to telnet from windows on port 3306 and I get a black screen with a blinking cursor and no way to go back but to close the shell.
Telnet from another ubuntu PC connects fine.

I have tried this from several Windows machines with no luck.

Any ideas on what could be happening?

Thanks in advance for any tips.

---

### Post by Stunts on 2008-12-17
Bump?

---

