---
title: "Samba, CUPS, and a Windows box."
date: 2008-12-21
forum: General Help
---

### Post by User X on 2008-12-21
I am trying to set up my Ubuntu machine to share it's printer with my windows machine and I am having trouble.  I have set up CUPS and Samba and I can add a printer with my windows machine and browse for a network printer and see the printers I have set up on my Ubuntu machine but when I go to install them I a get status of "access denied, unable to connect" instead of "ready" when it finishes instalation???

---

### Post by chrisamiller on 2008-12-21
Go to Systems > Administration > Printing

Right-click on your printer, make sure that it's shared and accepting jobs.  Also make sure that under 'access control', you're allowing printing for everyone.

---

### Post by XPuntu on 2008-12-23
I have all my settings as you suggested but still have the same error message as User X. My file sharing works just not printer sharing.

Thanks.

---

### Post by XPuntu on 2008-12-24
Got the answer here:

[http://ubuntuforums.org/showthread.php?t=806699&highlight=printer+sharing](http://ubuntuforums.org/showthread.php?t=806699&highlight=printer+sharing)

The bottom of post #1 describes how to get the ip address and port. Worked right away. Hope that helps you User X.

---

