---
title: "DCOP error?"
date: 2005-03-24
forum: Desktop Environments
---

### Post by silent82 on 2005-03-24
**** if I try to run kcontrol from shell I get:

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/silent82/.DCOPserver_port0__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
WARNING: DCOP communication problem!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
FATAL: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ERROR: KUniqueApplication: Can't setup DCOP communication.

**** If I remove all .DCOPserver_* from my home and I can load kcontrol from shell but when I try to launch an application from the Kmenu it doesn't load and when I try to open a folder  on the desktop it opens a small window that says:  KLauncher could not be reached via DCOP.

Anyone knows the reason and/or how to resolve this problem?

Tanks!

---

### Post by silent82 on 2005-03-24
And dcopserver is running:

silent82@port0:~ $ ps -A | grep dcop
15754 ?        00:00:00 dcopserver
15918 ?        00:00:00 dcopserver

---

### Post by ubuntu_demon on 2005-03-24
try removing :
~/.ICEauthority*

and :

sudo rm /var/tmp/kdecache-$USER/ksycoca*

and do a reboot

---

### Post by silent82 on 2005-03-27
[QUOTE=demon666_nl]try removing :
~/.ICEauthority*

and :

sudo rm /var/tmp/kdecache-$USER/ksycoca*

and do a reboot[/QUOTE]
 :-( nothing happens. Still have the problem.

---

### Post by Jeconais on 2005-03-27
Check the permissions of your .kde directory (and subdirectories), if they're set to root, sudo chown them to youself.

J

---

### Post by silent82 on 2005-03-27
[QUOTE=Jeconais]Check the permissions of your .kde directory (and subdirectories), if they're set to root, sudo chown them to youself.

J[/QUOTE]
 they all belong to me...

---

### Post by silent82 on 2005-03-27
The problem seems to be Konsole.
As soon as I start Konsole KDE Stops working correctly

---

### Post by Cap on 2005-05-15
[QUOTE=silent82]The problem seems to be Konsole.
As soon as I start Konsole KDE Stops working correctly[/QUOTE]

I have similar problem on Kubuntu, so i run kynaptic and reinstall dcoprss package. Now it works fine.
I hope this will help you.

Regards

---

### Post by geearf on 2005-07-29
Hello,

i still have this issue on one comp.

Also from time to time (usually when the bug happens i think) root becomes the owner of my .ICEauthority and .fonts.cache-1 .

I don't know why, and I can't find a way to fix it.

If you have any idea on this, thanks.

(I am using kubuntu by the way).

---

