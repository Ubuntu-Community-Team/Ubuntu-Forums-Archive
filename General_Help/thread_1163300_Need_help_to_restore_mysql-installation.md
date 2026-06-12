---
title: "Need help to restore mysql-installation"
date: 2009-05-18
forum: General Help
---

### Post by .gurkburk on 2009-05-18
I accidently messed up my mysql-installation, I started by trying to move the place mysql stores the actuall databases by using mv-command and editing the my.cnf file, I never got mysql to start after the move & edit, so I started trying to "fix it".

Ive tried alot of things, mostly fetched from various forums after googling, and now im left with a mysql that's completely messed up :/
I really need to get this up and running asap, I just cant figure out how.
Main problem is that the installation currently doesnt have a my.cnf in /etc/mysql  or a mysqld.sock in /var/run (I tried deleting alot of files manually, thinking they would be "generated" again as per default with a new installation).

Ive tried multiple variations of apt-get to get it to simply "do a fresh install" like the first time I ran:
sudo apt-get install mysql-server
But I cant get it to work.
Some commands ive varied and tried:
apt-get remove mysql-server --purge
apt-get autoremove
apt-get autoclean
apt-get --reinstall install mysql-server

I really just want a "fresh" installation of mysql...

---

