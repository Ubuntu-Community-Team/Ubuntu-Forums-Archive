---
title: "Weird Menu in GNOME Application"
date: 2006-06-21
forum: Desktop Environments
---

### Post by mamato on 2006-06-21
Hello, I just experienced this weird problem. Since I upgraded my ubuntu Box to the latest version of GNOME, every application has a weird appearance. It has "keyboard label" in every single item in the menu. You can see the screenshot here:
[CENTER] [IMG]http://img48.imageshack.us/img48/1346/weird5pp.png[/IMG]
[/CENTER]
  Can anybody help? Thank you.. :-D

---

### Post by dhaneshr on 2006-06-25
Yes, I'm experiencing the same here too. I would appreciate some help here. I use UBUNTU 6.06 LTS on a Dell Latitude D600

---

### Post by bryanlking on 2006-06-25
I read on these forums some time ago that this problem was related to locale settings.  Change your locale setting to something different like english/us and that may fix it.

Do a "dpkg-reconfigure locales"

---

### Post by dhaneshr on 2006-06-25
That worked. It seems that the default language somehow got set to :p nglish(Australia) after the gnome update. I simply set Administration->LanguageSupport->Default Language to English(US) .

---

### Post by mamato on 2006-07-05
thanxs alot! now all my application back to normal again :D

---

