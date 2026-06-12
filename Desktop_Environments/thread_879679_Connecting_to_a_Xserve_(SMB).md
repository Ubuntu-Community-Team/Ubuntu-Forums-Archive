---
title: "Connecting to a Xserve (SMB)"
date: 2008-08-04
forum: Desktop Environments
---

### Post by mariourk on 2008-08-04
Hi,

We have a XServe that shares it's files via SMB. This always worked fine with our clients running Ubuntu 7.10. Recently I upgraded a few to 8.04 and ran into trouble.

Say, I boot the computer, open up Writer and type some tekst. Now I want to save it on the server. So I click on the save-as button choose the network-share give the document a name and click on save.

Ubuntu 8.04 will prompt to enter a password for user 'guest' on the domain MSHOME. This always worked just fine with 7.10. How can I make it work again with 8.04?

I allready figured out that I can change MSHOME in /etc/samba/smb.conf. But this still has no effect.

Note that the XServe is not the Primairy Domain Controller. It has it's own list of users, so it is no use to check with the PDC.

I really hope this can be fixed...

---

### Post by mariourk on 2008-08-06
Bumb! Noone? :(

---

