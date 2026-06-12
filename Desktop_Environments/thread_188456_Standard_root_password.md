---
title: "Standard root password?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by ZijWePro on 2006-06-04
Hello all!
I've just managed to install Ubuntu succesfully on my system. Now I want to install my nVidia Display Drivers but I need to log in onto root in my shell. For this I did:
su root
Then it asked me for the password but I don't have one because it didn't asked me to define one at installing...
So my question is: What is the standard root password?
Many thanks in advance!
Jeroen van Zijp a.k.a. ZijWePro

---

### Post by oyvindaa on 2006-06-04
It's the same as your user password. Try it.

---

### Post by donpaco on 2006-06-04
in Ubuntu you have 2 choices:

1/ you don't use the root account but the sudo command, which password is the same as your first user created.

2/ you go to System/administration/users then
you choose the root account and change the password (select the checkbox to show system accounts)

---

### Post by bigken on 2006-06-04
hi login with your user name and password then open a terminal type **sudo passwd  **you will be asked for your password thenyou will be asked to ** Enter new UNIX password ;)**

---

### Post by ZijWePro on 2006-06-04
Hey, many thanks for helping me out guys! Made sense now.

---

