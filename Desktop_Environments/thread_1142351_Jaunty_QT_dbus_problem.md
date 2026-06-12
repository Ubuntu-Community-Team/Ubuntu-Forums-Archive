---
title: "Jaunty QT dbus problem"
date: 2009-04-29
forum: Desktop Environments
---

### Post by straks on 2009-04-29
Hi, 

After upgrading to jaunty, a friend has been exeperiencing some problems concerning the QT dbus implementation. 

Commandline error message (kile and kate confirmed, might be other kde programs as well): 
> symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol:
_ZN14QObjectPrivate15checkWindowRoleEv

I have tried reinstalling both libqt4-dbus and libdbus-qt3/libdbus-qt, didn't help.

Any suggestions?

Cheers

---

### Post by sir_guedes on 2009-05-04
Hi Straks,

I have the same issue.
Did you got some solution for this?

Regards

sir_guedes

---

### Post by ashmew2 on 2009-05-13
Quoting from launchpad : 

> libQTCore is in the usr/local/lib directory. I cd to it and run dpkg -S usr/local/lib/libQtCore.so.4
 The computer says:
 libqtcore4: /usr/lib/libQtCore.so.4.4.3
libqtcore4: /usr/lib/libQtCore.so.4
libqtcore4: /usr/lib/libQtCore.so.4.4

I would suggest just moving (or removing) those libraries from /usr/local/lib and seeing if Qt applications start to work.


        


It was a bug filed at : [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970)

---

