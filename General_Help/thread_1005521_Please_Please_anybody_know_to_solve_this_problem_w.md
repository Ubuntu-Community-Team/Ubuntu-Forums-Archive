---
title: "Please Please anybody know to solve this problem with naulius? Never get a goog answe"
date: 2008-12-08
forum: General Help
---

### Post by ravindukelum on 2008-12-08
when I try to log in to ubuntu 8.10 there is no I can't see desktop or anything giving some error message please help me to correct this problem.

error messages:

1.Nautilus cannot be used now, due to an unexpected error.

Nautilus cannot be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

################################################## ################################################## ########

2.The panel has encountered a fatal error

The panel could not register with the bonobo-activation server (error code: 3) and will exit.
It may be automatically restarted. 




Still I can use terminal and other applications using Gnome Do.Only I can not see desktop (icons ,dialogs,and panels)

---

### Post by wersdaluv on 2008-12-08
If it's fine with you, delete the configuration files here--> /home/user/.gconf/apps :D

---

### Post by f37u5g0d on 2008-12-08
I would try 
sudo apt-get purge bonobo 
and then
sudo apt-get install bonobo.

Nautilus is the file browser in ubuntu so that explains why you have no desktop or icons.

---

