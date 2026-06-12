---
title: "Thunderbird not flying...?"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by Balvinder25 on 2007-06-24
hi all,
        im fresh to ubuntu and and have another problem..the prob is i unable to download mail from my normal yahoo ac to the system using thunderbird. i managed to install freepops but couldnt get it configured..i found the config.lua file but dont know where and what changes to make.so please guys help me on this one as well ..ant help would really be appreaciated..
balvinder

---

### Post by arvevans on 2007-06-24
In your Thunderbird email client, go to:
[INDENT]Edit/Account Settings[/INDENT]

Add your Yahoo email account information for both incoming (POP Server) and outgoing (SMTP Server).
Use:
[INDENT]pop.mail.yahoo.com, SSL, Port 995
smtp.mail.yahoo.com, SSL, Port 465[/INDENT]

Thunderbird implements it's own email fetch and put procedures, thus you do not have to set up native Linux email handling to use Thunderbird.
_._

---

### Post by Balvinder25 on 2007-06-24
hi..thanks for the quick reply ..i tried feeding the information as you wrote ..but its just not accepting the password and keeps prompting me for the passwd again and again...i am 100% sure that the passwd is ok and the caps lock was chked ..so what do we do from here onwards..??

Balvinder

---

### Post by raul_ on 2007-06-24
OT:

 I just found the thread name funny :lol:

---

### Post by Balvinder25 on 2007-06-24
im sorry but i didnt quite catch tht >>>??

---

### Post by nanotube on 2007-06-26
instead of using freepops (which is kind of a pain), use the webmail extension. it is much easier, and takes advantage of extension update functionality built into tbird, so is automatically up to date when hotmail changes their site.

---

