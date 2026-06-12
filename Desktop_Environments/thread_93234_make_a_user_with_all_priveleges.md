---
title: "make a user with all priveleges"
date: 2005-11-21
forum: Desktop Environments
---

### Post by tazzik on 2005-11-21
Hi,
quite new to linux, and the login screen won't let me login as "root". I know there are loads of security issues but i REALLY don;t care. It says that "you cannot login as administrator on this screen" I want to be able to. How do I do it. I didnt make any other user so i cannot login unless I go to the recovery mode in GRUB. Also, can I make a user that can see and edit all folders everywhere on every drive and open every program, that isn't root and does not have to go through terminal to do it. 
Cheers (help soon becuase i'm using windows atm)
tazzik
UPDATE. 
HAving read other threads I see why not to use "root". So can I make a user that can do everything like root and how. I need and really want to make a user that can do everything.
thnaks in advance

---

### Post by jasonwvu on 2005-11-21
To do this I went into 
**system tools**
**login screen setup**
**security tab**
**select allow root user to login **

---

### Post by tazzik on 2005-11-21
I would but there is no way for me to get onto the gui is there. can I make a user usin terminal???

---

### Post by ajgreeny on 2005-11-21
Why do you insist that you should be able to do this?  There are ways to edit all your configuration files without getting into such a situation which will ensure you have backups available if things go badly.  Have a look at the ubuntu users guide at  [http://ubuntuguide.org/](http://ubuntuguide.org/)  which although mainly for Hoary 5.04 is also good in most cases for Breezy 5.10.

If you really must do something as root such as delete or edit files that are not yours you can do it in many ways, but be warned you may break everything and then not be able to boot up at all!

You can open files from a superuser session of whichever file manager you use (eg kdesu konqueror or gksudo nautilus) and you will then be able to edit them or delete them but BE CAREFULL, EVERYTHING MAY GO HORRIBLY WRONG.

Good luck, but don't say you were not warned if all goes to worms.

---

### Post by tazzik on 2005-11-21
ok, thanks but i'm not familiar with the terminology you are using. I need to make a user from terminal to be able to login and get to the gui (atm i cannot get a gui at all) so how can i 1. make a new user in terminal and 2. let root login
(in easy to understand terms please)
thanks so much people, great support and great distro

---

### Post by teaker1s on 2005-11-21
if you can login without gui then 'sudo startx'

---

### Post by tazzik on 2005-11-21
ok, it throws up a lot of error messages and other stuff. Is there a command that lets me make a NEW user from withing terminsl (not in a gui) I cannot get a gui atm, thats why i need a user, to login.

---

### Post by Sutekh on 2005-11-22
To make a new user and set the password for that new user from the command line you need a

```

sudo adduser <newuser>

```
Then you should be able to login with that <newuser>.

If this is your first user, and I guess it should be, then it should have sudo priviledges, as in what you were asking here[QUOTE=tazzik]Also, can I make a user that can see and edit all folders everywhere on every drive and open every program, that isn't root and does not have to go through terminal to do it.[/QUOTE]
The <newuser> you create *can* do everything provided you use a **sudo** command.  It's safer than logging in as root.  [Ubuntu Wiki - RootSudo]("https://wiki.ubuntu.com/RootSudo")

If the new user *doesn't* have sudo priviledges, then you need to follow [Ubuntu Guide - Allow More Sudoers]("http://ubuntuguide.org/#allowmoresudoers") to get that working.  



If you want to be able to see and edit and run all files and folders, you can use the [Ubuntu Guide - Browse Files Folders as Root]("http://ubuntuguide.org/#browsefilesfoldersasrootnautilus").  This should be used carefully though as you will be able to delete files you may want to keep.

---

