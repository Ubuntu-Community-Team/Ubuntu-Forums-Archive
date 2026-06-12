---
title: "Login Manager"
date: 2012-04-23
forum: Desktop Environments
---

### Post by WritersTear on 2012-04-23
How do I get back the Default GDM login manager window upon Ubuntu startup, without completly removing KDE? Not to happy with KDE login screen, having problems with it (randomly sometimes login and logs me back out).

---

### Post by PaulW2U on 2012-04-23
> **WritersTear said:**
> How do I get back the Default GDM login manager window upon Ubuntu startup, without completly removing KDE? Not to happy with KDE login screen, having problems with it (randomly sometimes login and logs me back out).

**sudo dpkg-reconfigure gdm**, select gdm and ok.

---

### Post by WritersTear on 2012-04-23
Okay I am assuming I Don't have GDM. I have Ubuntu with the Ubunti theme. 
Basically just typed in that command and said "gdm" is not installed.

---

### Post by PaulW2U on 2012-04-23
Then you will have lightdm installed.

Try **sudo dpkg-reconfigure lightdm**, select lightdm and ok.

---

### Post by WritersTear on 2012-04-23
Thanks mate that worked. :)Much appreciated.

---

