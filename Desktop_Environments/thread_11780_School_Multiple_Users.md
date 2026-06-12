---
title: "School: Multiple Users"
date: 2005-01-19
forum: Desktop Environments
---

### Post by bennyp on 2005-01-19
I have seset up an Ubuntu box at ny school. It worries me that Ubuntu by default gives the install user (the student account on this box) root access.
I wish to enable the root user and restrict the access rights of the student.

I enabled root with sudo passwd root

As it is now, I can open Synaptic using student's passwd.
I can use sudo as student

I would like to disable both of these acess rights for the student account so that the system will stay rock steady.
hopefully I will get Ubuntu installed on all the public terminals so i can demonstrate how we dont need windows anymore. so far only the curious have experimented with the Ubuntu box, I want to force them to use it >=)

---

### Post by blueplazma on 2005-01-19
You can just replace the student user with the administrative user in /etc/sudoers.  This should remove any ability to sudo possessed by the student account.

---

### Post by lildude on 2005-01-19
Hi bennyp

You should be able to disable this behaviour by commenting out or deleting all the usernames, except root and those users you wish to allow, in the /etc/sudoers file.

HTH

---

### Post by az on 2005-01-19
Or you could do it the other way around.  When installing, make the user the admin (you) and when your system is up and running, create a new user.  This new user (the student) will only have rights to his/her home directory.

You can still use sudo and do not have to create or give the root a password.

You can also tell gdm to boot right into any user's session, if you want to skip the login on boot.

If you remove the first user's sudo rights and forgot to make a root password, you will be stuck.

---

### Post by bennyp on 2005-01-19
[QUOTE=azz]Or you could do it the other way around.  When installing, make the user the admin (you) and when your system is up and running, create a new user.  This new user (the student) will only have rights to his/her home directory.

You can still use sudo and do not have to create or give the root a password.

You can also tell gdm to boot right into any user's session, if you want to skip the login on boot.

If you remove the first user's sudo rights and forgot to make a root password, you will be stuck.[/QUOTE]
 Thanks for the speedy replies, I will do this tommorrow. I wonder why I didnt think of this before, I didn't factor over the winter break, and when I got back to class I found it hard to do the test!

---

