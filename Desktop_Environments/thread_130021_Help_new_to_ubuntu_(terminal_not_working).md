---
title: "Help new to ubuntu (terminal not working)"
date: 2006-02-15
forum: Desktop Environments
---

### Post by hammered24 on 2006-02-15
Hi,
Im trying to install a program using the terminal i type su and when i try to enter my password no caricters type and after i hit enter it says

hammered@Hammered24:~$ su
Password:
su: Authentication failure
Sorry.
hammered@Hammered24:~$ su
Password: (cant type here)
su: Authentication failure
Sorry.

anyways thanks for reading

---

### Post by Robgould on 2006-02-15
You just need to type your password. As a security measure, you can not see what you type. Not even like this ****. It just stays blank. This is to prevent someone from learning the number of charachters in you passoword. It only appears you are not typing, you are. Just type your password and press enter.

---

### Post by hashimoto on 2006-02-15
If you have a stndard Ubuntu installation, then use sudo instead of su. su is not active in standard Ubuntu. So instead of:
```
su
command
```

do:
```
sudo command
```

Sudo will ask your user password, not super user password. And you won't see any typing on the screen when you enter the password.

---

### Post by kaamos on 2006-02-15
instead of su, type "sudo su".

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by anirban.sam on 2006-02-15
replace su with sudo, if u want a root, type : sudo passwd root to create a separate root passwd

---

### Post by hammered24 on 2006-02-15
Thank you everyone for your help
I can now use java :D 

How do i update firefox to 1.5?

---

### Post by kaamos on 2006-02-15
[QUOTE=hammered24]How do i update firefox to 1.5?[/QUOTE]

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

