---
title: "Server on Ubuntu Destop"
date: 2006-06-04
forum: Desktop Environments
---

### Post by TamANhs on 2006-06-04
Hello any1 .. i wanna setup 1 server in my home for website with php.. but i just a newbie in Linux :( .. cuz i want use GUI in server for easy setup or do something with me :D  .. That good idea for me rite ? .. any1 can tell me some idea :(  ...

---

### Post by Corvillus on 2006-06-04
If this is a seperate computer that will strictly perform server duties, probably the easiest way is to use automatic LAMP with the Ubuntu server install. Otherwise, if you are on a desktop box, you can get a LAMP stack fairly easily by doing this.
```
sudo apt-get install mysql-server
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install php5-mysql
sudo apt-get install php5-mysqli
```

---

### Post by TamANhs on 2006-06-05
*Then .. how can i setup phpmyadmin for php forum..  ? can help me about it ?*

---

