---
title: "root session login"
date: 2005-09-16
forum: Desktop Environments
---

### Post by triviaseeker on 2005-09-16
Hi everyone,  Must say I am impressed with Hoary.  I ma trying to change the permissions on my windows folder and am told i need to do this as root.  I have used my normal login password for doing admin tasks that require root privledges successfully.  I can't start a session under root though.  Is there something i am missing.  ta.

Lester

---

### Post by sethmahoney on 2005-09-16
You can't log in as root.  If you're using the terminal, type sudo before the command.  If you want to use the GUI with root access, try typing

sudo nautilus

In either case, it will ask for your password.  Just enter your normal user password.

---

### Post by triviaseeker on 2005-09-16
Thanks for the info

---

### Post by rplantz on 2005-09-16
[QUOTE=triviaseeker]Thanks for the info[/QUOTE]
 For command line work, you can do:
             Applications -> System Tools -> Root Terminal

---

