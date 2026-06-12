---
title: "Which Mysql should I download?"
date: 2009-04-16
forum: General Help
---

### Post by runnner on 2009-04-16
I want to install free MySQL Community Edition on Ubuntu, 
but I don't know which one on the following page is for installing on ubuntu, thanks for help!
[http://dev.mysql.com/downloads/mysql/5.1.html#downloads](http://dev.mysql.com/downloads/mysql/5.1.html#downloads)

---

### Post by Cheesemill on 2009-04-16
There's no need for you to download anything from the MySQL website as mysql is included in the Ubuntu repositories, simply type the following into a terminal:
```
sudo apt-get update && sudo apt-get install mysql-server mysql-client
```

Software should be installed like this instead of downloading it from a website as this way it has been thoroughly tested with Ubuntu. It will also be kept updated along with the rest of your system.

See [here]("https://help.ubuntu.com/community/InstallingSoftware") or [here]("http://www.psychocats.net/ubuntu/installingsoftware") for more info.

Cheesemill

---

### Post by justc001 on 2009-04-16
You can install Mysql from the repositories:

sudo apt-get mysql-server

---

