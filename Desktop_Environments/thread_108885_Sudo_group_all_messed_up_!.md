---
title: "Sudo group all messed up !"
date: 2005-12-27
forum: Desktop Environments
---

### Post by rollps on 2005-12-27
Hi everyone,

I am running Xubuntu (from a server install) and I wanted to add my user to the sudo group. In fact, what I wanted was to be able to turn off my PC without having to type my password (XFCE stuff).

As I don't have the Gnome GUI for user management, I started messing with users, groups and so on... with a console.

Now, I don't have any sound, I can't perform any operation with su privileges, I don't know what's going on basically :???: 

Here is all I did with the CL :

```
man sudoer
man user
man adduser
vi /etc/adduser.conf 
man useradd
useradd -D
man useradd
man usermod
usermod -G
usermod -G sudoer
usermod -G sudo
usermod -G su
man usermod
usermod -G sudo rollps
sudo usermod -G sudo rollps
useradd -D
usermod rollps
sudo usermod -G sudo rollps
man usermod
sudo usermod -G sudo rollps
usermod -G sudo rollps
man usermod
synaptic
su synaptic
sudo synaptic
gksudo synaptic
man adduser
adduser rollps sudo
sudo adduser rollps sudo
man visudo
man sudoers
visudo
sudo visudo
export EDITOR=mousepad && sudo visudo
sudo -K
ps -A
sudo -s -H
adduser rollps sudoers
sudo adduser rollps sudoers
sudo adduser rollps sudoer
sudo adduser rollps 
adduser rollps 
sudo adduser rollps 

```

quite a mess, isn't it ? :rolleyes: 

then I tried editing sudoers with visudo (recovery mode), following another thread and added :

```
Host_Alias HERE=xubuntu0
User_Alias PRIVILEGED=rollps
Cmnd_Alias ADMIN=/usr/bin/apt
PRIVILEGED HERE=ADMIN, NOPASSWD:ADMIN

```

so now I get :

```
rollps@xubuntu0:~$ sudo visudo
rollps is not allowed to run sudo on localhost.  This incident will be reported.
```

Thanks in advance for any help,
Happy Holidays :)

---

### Post by Zalbor on 2005-12-27
Not sure, but I think the group that allows sudo is 'admin'. So you'd need to type 'sudo adduser rollps admin'.

---

### Post by JanvL on 2006-01-06
Hi, had the same problem,

the command is:

useradd -G admin yourusername

you need to have root-access to run useradd however!
If you messed up your administator-rights and have not 
changed the root password, your in trouble I guess.

On [www.distrowatch.org](www.distrowatch.org) this item is discussed in the review over
Ubuntu.

Lots of success, Jan

---

### Post by rollps on 2006-01-06
yeah I figured it out
and as I couldn't have root access anymore, I had to reinstall Ubuntu #-o 
(like in the win times, looong time ago :D )
thanks

---

