---
title: "root passwd"
date: 2005-10-30
forum: Desktop Environments
---

### Post by senzacionale on 2005-10-30
Now i install ubuntu for test. I didn't set any passwd for root just for regular user so what is the passwd for root account!

I must say that ubuntu is very nice linux. Now i am in gentoo but maybe i will change it to ubuntu!

---

### Post by zekolas on 2005-10-30
The root account is disabled in ubuntu and most debian based distros for security reasons. Use the "sudo" command to gain root access. For example "sudo mkdir /opt/test" will allow you to creat a test directory in /opt, or "sudo gedit /ect/config will open gedit and allow you to edit configuration files. sudo uses your user password. To run an application as root just type "sudo appname".

I believe you can enable the root account by doing an "sudo passwd root" to enter a root password, then I believe you will be able to use the "su" command. However useing sudo instead of su, and leaving the root account disabled has many security benifits, so I would just get use to using sudo.

---

### Post by Kapre on 2005-10-30
[QUOTE=senzacionale]Now i install ubuntu for test. I didn't set any passwd for root just for regular user so what is the passwd for root account!

I must say that ubuntu is very nice linux. Now i am in gentoo but maybe i will change it to ubuntu![/QUOTE]

You can also check this [page]("http://www.ubuntuguide.org/#setchangeenablerootpassword") from the Ubuntu Guide on how to enable/change the root password

K

---

### Post by aysiu on 2005-10-30
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

