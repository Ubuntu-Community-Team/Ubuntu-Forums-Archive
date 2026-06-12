---
title: "Plesk 9 Installation Failure"
date: 2008-12-20
forum: General Help
---

### Post by poszest16 on 2008-12-20
I just tried to install Parallels Plesk 9 Panel and the installation failed half way though. I have been trying to fix the problem so much I can barely remember what caused the problem in the first place. But currently I'm stuck on psa install. If I run any thing like apt-get or dpkg it wants to repait the psa installation but it gets to a point where it attemps to make a test connection with mysql. First off it installed a custom install mysql so I can't seem to find any mysql config files but it can establish a connection and there is a mysql in /etc/init.d/ After research I found that plesk changes mysql root username to admin and makes the password the same as the plesk password but since the install failed half way I never established a account password. Can anyone help me manually remove psa or manually configure the password.

[APT-GET LOG]
START psa-9.0.0-ubuntu8.04.build90081117.17 installing (deb action: configure) AT Sat Dec 20 01:40:12 CST$
dpkg action:
 Trying to register service xinetd...  using /usr/sbin/update-rc.d
done
 Trying to restart service xinetd... done
Setting the default locale
The default locale is set to en-US (ENGLISH, UNITED STATES)


===> Installing rbash
 Checking that /bin/rbash registered as login shell...
/bin/rbash
 /bin/rbash is already registered as login shell

===> Installing psa database
 Trying to start service mysql... /usr/sbin/mysqld (pid 5504) is running...
done
 Trying to define valid mysql credentials...  Trying to establish test connection... ERROR 1045 (28000): $
failed
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'root'@'localhost' (us$
failed
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'root'@'localhost' (us$
failed
 Trying to establish test connection... ERROR 1044 (42000): Access denied for user ''@'localhost' to data$
failed
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (u$
failed
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'admin'@'localhost' (u$
failed
 Trying to establish test connection... ERROR 1044 (42000): Access denied for user ''@'localhost' to data$
failed
 Trying to establish test connection... ERROR 1045 (28000): Access denied for user 'root'@'localhost' (us$
failed
 Trying to establish test connection... Could not open required defaults file: /root/.my.cnf
Fatal error in defaults handling. Program aborted
failed
One more attempt to connect
STOP psa-9.0.0-ubuntu8.04.build90081117.17 installing (deb action: configure) AT Sat Dec 20 01:40:22 CST $

ERROR while trying to establish test connection

Aborting...

---

### Post by poszest16 on 2008-12-24
Can anyone help me. I can't even use apt-get anymore if I run "apt-get install some-application" It says "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
and "dpkg --configure -a" make the same problem as above.

PLEASE HELP ME!
J Greene

---

### Post by binbash on 2008-12-24
[http://forum.swsoft.com/showthread.php?t=55779](http://forum.swsoft.com/showthread.php?t=55779)

---

### Post by poszest16 on 2008-12-27
That topic is interesting and a little helpful but my problem differs a bit. First I did not upgrade this is a fresh install and second the file in /etc/psa/.psa.shadow is missing for some reason.

Also mysql starts fine but psa is trying to connect to mysql with blank password which is being denied. Before I installed Plesk I already had mysql installed and I think that might have something to do with it.

---

### Post by poszest16 on 2009-01-19
Problem Resolved: I Dumped Plesk. GOODBYE!!!
But Seriously The Reply Above Did Help The Problem.

---

