---
title: "Problem with root login on kubuntu using graphical interface"
date: 2007-08-21
forum: Desktop Environments
---

### Post by zeeshan4it on 2007-08-21
Hi,

I have installed kubuntu and in system settings -> user manager i enabled root login and assign it a password by using administrative privilages. Now i should be able to login as root but when i logoff from my personal login and try to login as root it still says root login is not allowed. How to fix that problem.

I know its not recommended to login as root but then in normal user login how can i copy/paste files. Also i m using dreamweaver on kubuntu and i have installed it after installing wine. Now if i login from my personal user then it does not allow me to save files on /var/www/mysites. 

If i use sudo -i then it only permits me to edit files with in the terminal but i want to do it via dreamweaver to edit/create php files.

How i can achieve this without login as root or how to login as root?

Any advice please?

Zeeshan

---

### Post by tzulberti on 2007-08-21
Hi. You could test:
"sudo su"

and then
"wine Dreamweaver" (or the location of Dreamweaver.exe)

There you should be running Dreamweaver so you shoud be able to edit the files...

---

### Post by mcduck on 2007-08-22
"kdesu konqueror" asks for you password and then opens the file manager as root. You can even create a launcher for that if you need it often.

This is much safer than actually logging in as root, as this way only the file manager (instead of _everything_) runs as root.

---

