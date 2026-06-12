---
title: "root user in gui"
date: 2007-12-22
forum: Desktop Environments
---

### Post by hyfather on 2007-12-22
I want to know how to do *sudo* tasks in the Ubuntu 6.06 GUI. Like, I am unable to get rid of read-only access to my WinXP mounted HDDs, I want full access, from the GUI!
The other day, I wanted to change a config file in /etc/ppp/peers, but I could open it in full access from the GUI in gedit.

---

### Post by bapoumba on 2007-12-22
To run a graphical application with root privileges, please use gksudo <app_name_here>.
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by t-bone510 on 2007-12-22
Why do gksu everytime when you can just chmod the drives... 

```
sudo chmod 777 -R /media/sda2
```

****REPLACE SDA2 WITH YOUR DRIVE NAME****

Now, you will always have access to write and read.

---

### Post by Prospero2006 on 2007-12-23
You can allow root logins in the kdmrc or gnome config file. That's what I do. 

(Ready, Aim, Flame the guy who logs into a graphical desktop as root!)

---

