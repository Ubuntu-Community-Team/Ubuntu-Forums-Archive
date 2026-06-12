---
title: "Can't get root permission in XFCE?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by denzilla on 2005-05-11
There are certain tasks within xfce that prompt for a password. I type my root password as I would normaly do in Gnome, but it keeps informing me that its wrong. I also cannot sudo passwd, either. Tells me I;m not a sudoers and action will be reported?

---

### Post by jcooper on 2005-05-12
You need to ensure your user account is a member of the sudoers group. The user account specified at login is added to this account, and you can sudo with the password for that account.

The message you receive is just sudo informing you that the attempted access to it has been logged on your local machine - i.e. nothing to worry about ;)

---

### Post by denzilla on 2005-05-12
[QUOTE=jcooper]You need to ensure your user account is a member of the sudoers group. The user account specified at login is added to this account, and you can sudo with the password for that account.

The message you receive is just sudo informing you that the attempted access to it has been logged on your local machine - i.e. nothing to worry about ;)[/QUOTE]

Thanks :)

I understood what the  "will be reported"  thing was about. I immediately punished myself for my actions afterward.  \\:D/

---

