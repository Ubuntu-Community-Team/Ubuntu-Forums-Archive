---
title: "SUID Password"
date: 2006-08-26
forum: Desktop Environments
---

### Post by Desi-Wiz on 2006-08-26
Pardon me if this has been discussed to death... I just recently installed Ubuntu 5 and sort of zoomed thru the instal but did setup one user account during the process - do not remember seeing anything that offered me to setup a password for the SUID root so as you see I cannot login using root. I can however login using the account I setup during the install but I would like to have the root account setup so my questions are:

- How do I setup a password for the root account without doing re-doing the instal
- I cannot even see the root account in the users and groups - where do I set it up.

Thanks much in advance.

---

### Post by Ramses de Norre on 2006-08-26
Read [this]("http://wiki.ubuntu.com/RootSudo").
If you then still want to enable the root acount you can run ```
sudo passwd root
``` but I wouldn't if I were you.

---

