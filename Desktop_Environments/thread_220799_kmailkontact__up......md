---
title: "kmail/kontact ******* up....."
date: 2006-07-22
forum: Desktop Environments
---

### Post by rockprincess on 2006-07-22
hello everyone,

i'm desperate, and dunno how to fix my problem with kmail/kontact - it happens that my emails "disappear" - whenever i click on them to read them/mark them as read some of them disaappear and their "senders name" "subject" and "date" turn into "Unknown" and infact the whole content of the email is gone

i've attached a screenshot to demonstrate my problem (unfortunately it's only in german, but i hope you'll get the idea!)

---

### Post by rockprincess on 2006-07-30
solved haha!

very special thanks to Ingo Klöcker from the KDE Mailinglist Team, who told me to change the permissions of my kontact/kmail folder as it was imported from cd/dvd and the permissions on cd/dvd are only "readable" and not writeable.

so, it should like that:

```
chmod -R u+w ~/.kde/share/apps/kmail/mail
```

or to change the whole .kde folder

```
chmod -R u+w ~/.kde/share/apps/kmail/mail
```

thank you :D

---

