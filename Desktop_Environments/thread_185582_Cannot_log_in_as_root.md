---
title: "Cannot log in as root"
date: 2006-05-31
forum: Desktop Environments
---

### Post by remyr on 2006-05-31
How do I log in as root? It did not give me an option to set up the root account during the install and my regular password does not work nor does leaving the password field blank. According to the Users and Groups app under the Administrative menu I have Adminstrator rights but when I try to edit my /ect/apt/sources.list file it says I have to be logged in as root. What gives? I am trying to install the Demudi packages but I can't add the repository to my sources becuase of this. Thanks.

Remy

---

### Post by tonyr on 2006-05-31
The Ubuntu convention is to not have a **root** account.  For root privileges,
precede any command with **sudo**, as in
```

sudo nano /etc/apt/sources.list

```

(or the editor of your choice). It will prompt for a password. Enter **your** password.

EDIT: See [https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by aysiu on 2006-05-31
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by |nferno on 2006-05-31
try sudo vi /etc/apt/sources.list 

sudo <comand> allows you to run commands as a superusers it will ask you for a password and you just enter you normal user password.

if you want to run a shell as root sudo -s but i don't think this is a very wise idea.

to give other users sudo rights add them to the /etc/sudoers file

---

### Post by remyr on 2006-05-31
Wow! Thanks guys! Never before have I ever been to a forum where I recieved a single reply within 5 minutes, much less three! Very impressed here!

Remy

---

### Post by jones_jj on 2006-06-01
I believe if you want to add a password to root, you'll have to do **sudo passwd root** and that should allow you to add a password to root.

The reason why you weren't given an option to add a password to root is because you did a normal install of Ubuntu.  If you would have done an expert install you get the option to give a root password.

---

### Post by tonyr on 2006-06-01
[QUOTE=remyr]Wow! Thanks guys! Never before have I ever been to a forum where I recieved a single reply within 5 minutes, much less three! Very impressed here!

Remy[/QUOTE]

It's part of the meaning of **Ubuntu**.

---

