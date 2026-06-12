---
title: "Making GDM Remember users password"
date: 2005-09-27
forum: Desktop Environments
---

### Post by laffo on 2005-09-27
I have setup a ubuntu box for my parents to use, but my mum is not very good with computers. Is there a way (other than setting a null password, dont want to do that as i will have ssh running) to make GDM remember users passwords so all they have to do is click on their picture/name?

---

### Post by nocturn on 2005-09-27
[QUOTE=laffo]I have setup a ubuntu box for my parents to use, but my mum is not very good with computers. Is there a way (other than setting a null password, dont want to do that as i will have ssh running) to make GDM remember users passwords so all they have to do is click on their picture/name?[/QUOTE]

Modify /etc/pam.d/gdm to not require passwords.  It will still request a password on the consoles and SSH.

---

