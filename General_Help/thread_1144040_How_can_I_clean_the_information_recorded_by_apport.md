---
title: "How can I clean the information recorded by apport?"
date: 2009-04-30
forum: General Help
---

### Post by Pidgin on 2009-04-30
I am making a customized version of Ubuntu. A problem occured during the install of a specific package. But then I fixed that problem. However, I thought apport had recorded that, which led to an annoying result. Each time a user installed my version of Ubuntu, he would complain. Because the first time the system booted, apport would tell the user that a package crashed during the install, and ask the user to report the problem. Though actually that problem had been solved by me, the user still doubted whether my version of Ubuntu was unstable. Please tell me how to clean the information recorded by apport.
Thank you!

---

### Post by cariboo on 2009-04-30
The apport log is in /var/log/. Have a look a the [Apport Wiki]("http://wiki.ubuntu.com/Apport")

---

### Post by Pidgin on 2009-05-01
It seems that /var/crash is suspicious.

---

