---
title: "Workbench on kde [kubuntu] error"
date: 2020-02-29
forum: Desktop Environments
---

### Post by trelozakinthinos on 2020-02-29
Hello,
I am using Kubuntu 19.10 and I installed mysql workbench (from apt and directly from mysql site) and I cannot connect to database.
When I am creating a connection and hit "Test connection" an error occur which says 

```
the name org.freedesktop.secrets was not provided by any .service files
```

As I read about it tries to find the gnome-keyring for storing the password.

I can install it but I do not know if it will break or collate with something on my machine.
I have no idea if kde has something simillar and it is no good idea to install it.

---

### Post by SeijiSensei on 2020-03-01
KDE has a "wallet" system for storing passwords.  (Look in System Settings > Account Details.)  I have no idea if that will work with mysqlbench. I usually just run the native SQL clients like mysql or psql from the command prompt and type SQL commands directly. On rare occasions I use Microsoft Access with ODBC.

> from apt and directly from mysql site

What does this mean? Surely you don't have both installed.  I'd stick to the version in the repositories.

---

### Post by trelozakinthinos on 2020-03-01
I mean that I downloaded through the repository (apt install mysql-workbench) and directly from MySQL site (deb file).
Not both together, one at a time.
So the solution would be the guys that make workbench to include kde wallet? Or can I do something to work.

---

### Post by CelticWarrior on 2020-03-01
> **trelozakinthinos said:**
> I mean that I downloaded through the repository (apt install mysql-workbench) and directly from MySQL site (deb file).

But did you actually installed the -deb you downloaded? If so, supposedly, a newer version superseded the one from the repositories. The actual version you're running is what matters.

---

### Post by trelozakinthinos on 2020-03-07
Sorry for the delay (I do not get email notifications for replies, any ideas)

I purge the installation from the apt. So I installed only the latest now (MySQL Workbench CE (GPL) 8.0.19 CE build 15713499) and from repository is this version (mysql-workbench/eoan 8.0.17+dfsg-1ubuntu2 amd64)
Both the same problem.

Where should I post this? To mysql or ubuntu-team? And how do I do that. I have never done this before.

---

### Post by deadflowr on 2020-03-07
> Where should I post this? To mysql or ubuntu-team? And how do I do that. I have never done this before.
For the version from Ubuntu's repository you report it to Ubuntu.
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

The version not from Ubuntu's repository will probably have its own problem reporting mechanism, which I don't know what it is.

---

