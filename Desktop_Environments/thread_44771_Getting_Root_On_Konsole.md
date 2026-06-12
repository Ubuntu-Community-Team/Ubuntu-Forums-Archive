---
title: "Getting Root On Konsole"
date: 2005-06-27
forum: Desktop Environments
---

### Post by alec on 2005-06-27
Hi, I am new today to Kbuntu. So I am just working my way arround. 

I wanted to install some extra packages via dpkg, but cannot get Konsole to accept my user password to get to root.

I tried Ubuntu yesterday and had no problem with this.

I am assuming that there is something I am missing here. 

By the way I tried both su in a normal session and root shell sessions.

Any help in this matter will be appreciated.

---

### Post by apollo2011 on 2005-06-27
Welcome to the forum alec! :)

Are you using sudo? (K)Ubuntu doesn't act the same way most other distros work when it comes to root.  Instead of loggin in as root to do something, you use sudo and then the command.  So you would do:
$ sudo dpkg -i <package name>.deb

This would then ask for a password, where you would enter your user password, NOT a root password you may have assigned.

---

### Post by alec on 2005-06-27
Don't you hate it when its something so obvious. No root, so sudo!!!

No I was not using sudo... I will be from now on though.

Just one thought though yesterday when I was giving Ubuntu a look, what ever shell you use in Gnome took the normal su + password to give a root session.

Anyway many thanks for the help you have made me very happy.

---

### Post by uberlinux on 2005-06-27
[QUOTE=alec]Don't you hate it when its something so obvious. No root, so sudo!!!

No I was not using sudo... I will be from now on though.

Just one thought though yesterday when I was giving Ubuntu a look, what ever shell you use in Gnome took the normal su + password to give a root session.

Anyway many thanks for the help you have made me very happy.[/QUOTE]
I like to be bad and right after the install, I will go..
sudo PASSWD, and enter a new root password, then
su into root.  
naughty, I know \\:D/

---

### Post by alec on 2005-06-27
[QUOTE=uberlinux]I like to be bad and right after the install, I will go..
sudo PASSWD, and enter a new root password, then
su into root.  
naughty, I know \\:D/[/QUOTE]

There is some naughty but nice stuff on this forum. I just don't know if it the right sort of place for a boy like me...

---

### Post by fdoving on 2005-06-28
[QUOTE=alec]There is some naughty but nice stuff on this forum. I just don't know if it the right sort of place for a boy like me...[/QUOTE]
 In addition to this forum i can suggest the IRC channel #kubuntu on irc.freenode.net

---

### Post by nocturn on 2005-06-28
sudo su -

---

