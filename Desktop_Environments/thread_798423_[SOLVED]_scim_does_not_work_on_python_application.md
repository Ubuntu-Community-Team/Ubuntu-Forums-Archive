---
title: "[SOLVED] scim does not work on python application"
date: 2008-05-18
forum: Desktop Environments
---

### Post by gobi on 2008-05-18
I am using ubuntu 8.04 hardy. I tried to use software Anki which is built on Python. But SCIM input method does not work. It works with no problem with other programs.

Could someone help me please.

---

### Post by gobi on 2008-05-20
Buzz

---

### Post by fdimmling on 2008-05-20
> **gobi said:**
> I am using ubuntu 8.04 hardy. I tried to use software Anki which is built on Python. But SCIM input method does not work. It works with no problem with other programs.

Could someone help me please.

It is not true that SCIM does not work with Python applications. I am using CDict, a Chinese dictionary program written by myself in Python and it works well with SCIM in Hardy. The reason must be somewhere else. I have seen that Anki is built with the Qt libraries, while my program uses Gtk. I had sometimes problems to use SCIM with Qt applications in earlier versions of Ubuntu but there was always a solution. At present I do not use a Qt application with SCIM. BTW Have you installed scim-bridge-client-qt, which makes scim-bridge available to Qt programs?

Friedrich

---

### Post by gobi on 2008-05-20
Friedrich

Thank you for reply.

I have checked and installed scim-bridge-client-qt4 and python-qt4. 

But it still can not input in japanese. What else should I check?

---

### Post by fdimmling on 2008-05-20
Do you have other packages installed using the Qt library, e.g. any KDE programs? Does it work there?

Friedrich

---

### Post by gobi on 2008-05-21
Friedrich

Thanks for reply, I will check that when I go home, right now I am at office. Maybe it was not working. Also, yesterday I tried Java program (jMemorizer) and SCIM did not work with it too. But I wonder that SCIM was working with Eclipse which is also Java application !?

Gobi.

---

### Post by gobi on 2008-05-21
SCIM does not work with KDE applictions for example I tried with Basket Note Pads

---

### Post by gobi on 2008-05-24
Problem has dissappeared after I reinstalled ubuntu. Looks something went wrong when I upgraded my distro by online upgrade.

---

### Post by fdimmling on 2008-05-26
> **gobi said:**
> Problem has dissappeared after I reinstalled ubuntu. Looks something went wrong when I upgraded my distro by online upgrade.

That's why I a always make a fresh install. 

Friedrich

---

### Post by aeriph on 2010-12-24
Just to let people know, it's often not necessary to reinstall the OS to get SCIM working in Anki. Found this article with explanation:

[http://eastasiastudent.net/1442/study/scim-anki/](http://eastasiastudent.net/1442/study/scim-anki/)

---

