---
title: "sudo and su??"
date: 2009-05-10
forum: General Help
---

### Post by abhilashm86 on 2009-05-10
i'd never bothered about the difference untill my friend asked it, 
when we type 
sudo su - means we are root to perform special actions,

when we type 
su 
shell asks for password, when we give password same as sudo/login, it dosen't accept, why is this.
whats difference between sudo and su.....

---

### Post by FIONEX on 2009-05-10
I don't think that ubuntu has a true root user.  I'm not too sure but su is supposed to log you in as the root user, and it's not setup by default.  sudo just upgrade your privileges.  if you do sudo -l, then it's like logining in as root.

---

### Post by abhilashm86 on 2009-05-10
yes i get the point, if su is root, then why use sudo?? see the error we come across, is there any procedure so by typing su, can't we login as root??

```
abhilash@abhilash:~$ su -l
Password: 
su: Authentication failure
abhilash@abhilash:~$ sudo su
root@abhilash:/home/abhilash# 

```

---

### Post by bacardiandwatermelon on 2009-05-10
When you use sudo.. You type in your login password.
When you use su.. You type in your root password.

[http://kb.iu.edu/data/amyi.html]("http://kb.iu.edu/data/amyi.html")

---

### Post by abhilashm86 on 2009-05-10
yes fine, thanks, i get to know now the usage..........

---

### Post by bodhi.zazen on 2009-05-10
See [uwiki]RootSudo[/uwiki]

both su and sudo give root access.

su = root password and is all or none.

sudo = users password and can be configured to allow root assess to some but not all of the OS.

sudo has many more options and configuration choices.

there are (minor) differences in how they handle environmental variables (such as $HOME) as well.

See : [http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Compare that to [http://unixhelp.ed.ac.uk/CGI/man-cgi?su](http://unixhelp.ed.ac.uk/CGI/man-cgi?su)

---

### Post by CatKiller on 2009-05-10
The main difference is that su stands for "switch user." You can switch user to any user with su by giving that user's password. If you don't give a user to switch to, it defaults to switching to root, since that's the most likely circumstance that you'd want to switch user, and then you need to give root's password. However, on an Ubuntu system, root doesn't have a password by default, and so you can't use su to switch to the root user.

Instead, Ubuntu uses sudo, a mechanism to run the given command as root, but only requires the user's own password (switch user/do). Access to which users can do what as another user is quite fine-grained.

sudo su is an edge case that lets you switch to root, but using the user's own password. This is for those users who are used to being able to su to root but can't because there's no root password.

---

### Post by abhilashm86 on 2009-05-11
> **CatKiller said:**
> The main difference is that su stands for "switch user." You can switch user to any user with su by giving that user's password. If you don't give a user to switch to, it defaults to switching to root, since that's the most likely circumstance that you'd want to switch user, and then you need to give root's password. However, on an Ubuntu system, root doesn't have a password by default, and so you can't use su to switch to the root user.

Instead, Ubuntu uses sudo, a mechanism to run the given command as root, but only requires the user's own password (switch user/do). Access to which users can do what as another user is quite fine-grained.

sudo su is an edge case that lets you switch to root, but using the user's own password. This is for those users who are used to being able to su to root but can't because there's no root password.

very well described catkiller, thanks a lot, yea the security of linux in network is at great height.............

---

