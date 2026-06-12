---
title: "Kontact (K-Mail) very slow in Ubuntu Edgy"
date: 2006-12-20
forum: Desktop Environments
---

### Post by johatte on 2006-12-20
I'm running Ubuntu Edgy with Gnome desktop. As my e-mail application I'm using K-Mail (there are many strong reasons for that). After starting K-Mail it takes very long time to get it up and running. There are no errors, because the program is functioning otherwise fine. 
Why? Is there any remedy for the slow start up? 
Thank you in advance for your kind help.

---

### Post by crumja on 2006-12-20
Using cross-desktop environment applications is not a good way to help performance. Kontact is a Qt app, and you're using it in a mostly GTK environment. The only problem is that the Qt and KDE libraries aren't loaded, so Kontact must drag a whole bunch of stuff with it into memory. Whereas if you were running in KDE, the KDE and Qt libraries would already be in memory and startup would be pretty quick.

There's a reason that most people avoid using cross-desktop applications. Consider switching to Evolution if you can. What is specific to Kontact that makes it essential?

---

