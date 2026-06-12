---
title: "Connecting to a WIndows Domain"
date: 2005-12-08
forum: Desktop Environments
---

### Post by sjb on 2005-12-08
I need to connect my laptop to the companies windows domain. So that I can download mail and access fileservers. I have NO access to the windows domain controller other than to identify myself. So attaching a linux samba PDC to the windows domain controller is not going to happen.

My situation is I work in France and have a french desktop with windows on (but its a french language install of windows and a french keyboard) as I am english I am allowed to use my own personnel laptop, however, it runs ubuntu. My mail is on a windows exchange server but to access it I have to be identified on the windows domain controller.

How do I configure my ubuntu laptop to logon to the windows domain, when I logon to my laptop ?

---

### Post by ritger on 2005-12-10
Have you tried [Winbind]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html")?

---

