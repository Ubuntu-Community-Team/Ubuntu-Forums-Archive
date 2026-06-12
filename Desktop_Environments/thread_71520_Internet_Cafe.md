---
title: "Internet Cafe"
date: 2005-10-03
forum: Desktop Environments
---

### Post by almuwatta on 2005-10-03
Hey everyone

       Opening up The first Open Source Cafe in my area, will run Ubuntu on the desktops.  trying to figure out how to time the logins of each machine via cronjob -- any ideas to lead me on this path -- 
             Thanks

---

### Post by KingBahamut on 2005-10-03
[http://howtos.linux.com/howtos/XFree-Local-multi-user-HOWTO/examples_dm.shtml](http://howtos.linux.com/howtos/XFree-Local-multi-user-HOWTO/examples_dm.shtml)
Bout 25% way down the page.

---

### Post by almuwatta on 2005-10-06
does this file has to set on every computer.   and forgive the new guy question, but to get every machine to log into one( Server) I set up a NIS server right ?

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=almuwatta]does this file has to set on every computer.   and forgive the new guy question, but to get every machine to log into one( Server) I set up a NIS server right ?[/QUOTE]
NIS will allow you to have the list of users/passwords stored on server, and each client machine using this list to allow user's login. You also need to take care of users' home directories, to make each directory available to client machines - usually done by mounting them via NFS. This is what is done in most corporate/university settings. There are detailed guides and HOWTOs - use google to find them.

---

