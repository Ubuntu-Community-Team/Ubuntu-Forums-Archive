---
title: "Can not remove sudo"
date: 2005-09-16
forum: Desktop Environments
---

### Post by easydisk on 2005-09-16
Kubuntu with KDE 3.4.2-0ubuntu0hoary2, but it is not a special KDE problem.

I have a little strange sudo... I preffer to remove the sudo package and use it the old way, with su and give the root password. I already have given the user root a password but I still can not remove sudo.. because than I can not start applications from the desktop with root rights. (KDE property of desktop icon => advenced => run as user 'root', the kde-su programm is called which ask me for a password and then the application is started)

BUT I have to give the current user password and not the root password to start the applications !!! 

So. I want to give the root password (and ONLY the root password, not the user password !) and disable sudo or remove sudo completely, but how ?

---

### Post by FLeiXiuS on 2005-09-16
The sudo package is very dependant in Ubuntu.  I wouldn't advise removing it.  Plus it poses a huge security benefit to use sudo over su.  SU will allow all users to access a root password prompt.  I don't like that idea, some may but I just don't.  Sudo can do almost if not all of what su can do.  

In my opinion, I'd reccomend keeping it.

The root account is disabled by default.  You don't need it if you have sudo.  Hence a huge security bonus.

---

