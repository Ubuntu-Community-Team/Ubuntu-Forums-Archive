---
title: "Running MySQL Administrator"
date: 2006-07-01
forum: Desktop Environments
---

### Post by matthorton on 2006-07-01
Hello everyone

I've just installed mySQL Administrator from a tar.gz file and i can seem to run the application.

i followed these instructions exactly...

"To install MySQL Administrator, run this command:

shell> tar --directory=/opt -xzvf mysql-administrator-version-linux.tar.gz

This installs the application binary in /opt/mysql-administrator/bin. Change into that directory and run mysql-administrator to start the application.

Distribution-specific packages will be available at some point."

...I have done this but it doesn't install to the path is says it should.

Mine installed to here "/opt/mysql-administrator-1.1.10" and a "bin" directory does not exist there.

Has anyone else experienced this problem or can anyone see what I'm doing wrong?

Thanks ever so much in advance. I'm having such trouble.

Matt.

---

### Post by Ctrl+Alt+Del on 2006-07-01
why not install it from the repos, the package is named mysql-admin

---

### Post by matthorton on 2006-07-01
is that using the command

sudo apt-get install mysql-admin?

---

### Post by Ctrl+Alt+Del on 2006-07-01
Yes, or simply via the add/remove option in your Applications Menu

---

### Post by matthorton on 2006-07-01
its strange, i cant find it in the add/remove list. even when i search for it in advanced mode.

when i type "sudo apt-get install mysql-admin"

i get this...

"matt@Ubuntu:~$ sudo apt-get install mysql-admin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mysql-admin"

---

### Post by Ctrl+Alt+Del on 2006-07-01
It's in the universe repo (System Administration), maybe you haven't yet enabled it?

---

### Post by makadam on 2006-07-29
The MySQL Aministrator (V. 1.1.6) you can install from the Ubuntu repository is buggy. You are not able to access the User Administration tab without a freez of the tool. This probleme is already known and resolved ([http://bugs.mysql.com/bug.php?id=13138](http://bugs.mysql.com/bug.php?id=13138)) so it is a good idea to use the newest MySQL Administrator (V 1.1.10 or higher). Ubuntu schould ubdate this repository asap.

---

### Post by az on 2006-07-29
> **makadam said:**
> Ubuntu schould ubdate this repository asap.

Did you file a bug report?

---

### Post by makadam on 2006-08-03
Hi azz.

There exists already an bug report : (Bug #29802:
MySQL Administrator Locks when trying to do User Administration).
Also there exists a workaround, mentioned in the bug report to ease the problem: ```
export DEBUG_DONT_SPAWN_FETCHES=1
mysql-admin
```

---

### Post by Dyst Mingus on 2006-08-20
i added the line:

DEBUG_DONT_SPAWN_FETCHES=1

to the end of my /etc/profile and it no longer hangs when accessing the user administration tabs.

---

