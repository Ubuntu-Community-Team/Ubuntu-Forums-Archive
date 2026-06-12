---
title: "Dual Monitors 8.10 on ATI card"
date: 2009-03-04
forum: General Help
---

### Post by CrusaderAD on 2009-03-04
I have an ATI HIS X1550 graphics card and I am trying to use dual monitors. Any suggestions on how to do so? Everything I see is for nvidia cards.

---

### Post by CrusaderAD on 2009-03-04
Sort of like the "Extend my Desktop to this Monitor" in Vista.

---

### Post by linuxisevolution on 2009-03-04
Find the drivers for your card first. You may be able to configure it anyway with System >> administeration >> Screen Resolution. and Click "Clone Monitors". That's all I know right now. I'll look into it tomorrow, I'm going to sleep now.

---

### Post by linuxuser21 on 2009-03-04
This one was a very hard one for me and I could not find an answer anywhere; however, I've successfully done it.  I installed EnvyNG. [Here]("http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/") is the website I followed.

---

### Post by CrusaderAD on 2009-03-05
EnvyNG worked like a charm. Here's some quick instructions for the post:

```
sudo apt-get install envyng-core envyng-gtk envyng-qt
```

The ATI settings were in Applications > Accessories > ATI Catalyst Control Center.

Thanks!

---

### Post by linuxuser21 on 2009-03-05
Glad I could help!

---

