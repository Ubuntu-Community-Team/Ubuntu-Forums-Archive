---
title: "GDM language"
date: 2005-05-06
forum: Desktop Environments
---

### Post by fluxus on 2005-05-06
Hello everybody,

this is my first post in this forum. I changed from Gentoo to Ubuntu 2 days ago and I'm very content with it (although I like Gentoo very much too but I've become to impatient to compile everything).
So everything works very fine in Ubuntu but a little cometic issue:
The first time GDM is started the login screen is English instead of German (like the rest of my system). When I restart GDM - even without having logged in before - it turns to German. I think it has something to do with the GDM_LANG variable. I tried to add ```
GDM_LANG=de_DE.UTF-8
``` to /etc/environment but that didn't help. The rest of /etc/environment is:
```
LANGUAGE="de_DE:de:en_GB:en"
LANG=de_DE.UTF-8
```
Does anybody know a proper solution to permanently change the language of GDM to German?

---

### Post by free on 2005-05-19
Add something like [FONT=Courier New]LANG="sk_SK.UTF-8"[/FONT]  to your /etc/default/gdm.

Works for me.

---

