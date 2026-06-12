---
title: "mythtv install error"
date: 2006-04-05
forum: Desktop Environments
---

### Post by n_hendrick on 2006-04-05
I followed the how-to to install mythtv in breezy, everything went a'okay until the last step when mythtv-database trys to login as root. I get the following error....

Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database

anyideas how to remedy this block...I've tried everything...I've googled, searched forums to no avail. I would very much like to get mythtv to work.

---

### Post by !nkubus on 2006-04-05
did your how-to was this one?

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

there is a section with mysql in there it might help

---

### Post by n_hendrick on 2006-04-06
I already went through that how-to, I've tried everything, uninstalling and reinstalling, trying to setup mysql manually....there has to be a way to get that mythtv-database thing to install and setup through apt-get which is what I'
m trying for...I don't think they would have the package available if it doesn't work automatically. Anyway, I might just have to scrap it because I get the error everytime I run apt-get...so oh well.

---

