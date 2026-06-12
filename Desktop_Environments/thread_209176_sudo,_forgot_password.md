---
title: "sudo, forgot password"
date: 2006-07-04
forum: Desktop Environments
---

### Post by malfist on 2006-07-04
I have been running Ubuntu 5.10 and I have forgotten the password for sudo. I can still login, I didn't set the passwords the same. Is there anyway I can reset the sudo password, without reinstalling Ubuntu?

---

### Post by meng on 2006-07-04
The password for sudo is the same as your user password.

---

### Post by aysiu on 2006-07-04
This may help: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by malfist on 2006-07-04
[QUOTE=meng]The password for sudo is the same as your user password.[/QUOTE]

Sorry, but that is not true, you set the sudo password seperatly.

[QUOTE=aysiu]This may help: [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)[/QUOTE]

Does that mean if a launch recovery mode I can use the sudo password command and reset the password?

---

### Post by Jagot on 2006-07-04
If you are the only user on the system then the password you set for your username is the one that you need when running commands that require sudo.  Sudo password is not setup separately, unless you're talking about setting up other users with admin privileges.

From the wiki ([https://help.ubuntu.com/community/RootSudo):](https://help.ubuntu.com/community/RootSudo):)

> By default, the root account is locked in Ubuntu. This means you cannot login as root or use su. Instead, the installer will setup sudo to allow the user that is created during install to run all administrative commands.

This means that in the terminal you can use sudo for commands that require root privileges. All programs in the menu will use a graphical sudo to prompt for a password. When sudo asks for a password, it needs YOUR USER Password; this means that a root password is not needed.

If you can't access sudo with your user password then there may be something wrong with your sudoers file, so see aysiu's post.

---

### Post by malfist on 2006-07-04
su -c 'make install'
password:
su: Authentication failure
Sorry.

it isn't the same.

---

### Post by Jagot on 2006-07-04
[QUOTE=malfist]su -c 'make install'
password:
su: Authentication failure
Sorry.

it isn't the same.[/QUOTE]

You were talking about sudo, not su.  Su is the root user, the pasword for which is randomly generated and thus you cannot access it, unless you set up a root user properly.

---

### Post by scxtt on 2006-07-04
sudo and su are 2 different things ... sudo uses _your_ password and su uses the _root_ password (if there is one) ...

run:
[indent]sudo 'make install'[/indent]instead ... if you want to be root, do:

```
sudo su -
```and enter **your** password ...

---

### Post by malfist on 2006-07-05
My mistake, I thought sudo and su was the same.

Sorry
Malfist

---

