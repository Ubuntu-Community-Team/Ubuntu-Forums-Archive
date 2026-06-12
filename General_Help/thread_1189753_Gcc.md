---
title: "Gcc"
date: 2009-06-17
forum: General Help
---

### Post by pronto32 on 2009-06-17
Hi guys i'm new to ubuntu.I've heard it's great and i wanted to install mysql in it.When i tried to unzip the mysql file in /usr folder that is the file system i got the msg sayin "you don't have the permission to do that".So i loged in as super user By giving $su -user name
and password.still the same problem.
Secondly i wrote a simple program and wanted to dbug it >when i gave gcc in the command prompt is got a msg sayin no such command how do i add gcc to my ubuntu where is it available.?
Pls help

---

### Post by dcstar on 2009-06-17
> **pronto32 said:**
> Hi guys i'm new to ubuntu.I've heard it's great and i wanted to install mysql in it.When i tried to unzip the mysql file in /usr folder that is the file system i got the msg sayin "you don't have the permission to do that".So i loged in as super user By giving $su -user name
and password.still the same problem.
Secondly i wrote a simple program and wanted to dbug it >when i gave gcc in the command prompt is got a msg sayin no such command how do i add gcc to my ubuntu where is it available.?
Pls help

Why not just use the Package Manager to install things?, that is what it is for.

---

### Post by Yellow Pasque on 2009-06-17
Mysql is installable from the repository. Install the build-essential package for gcc
In Ubuntu, prefix commands with *sudo* to run them as root.

---

### Post by leg on 2009-06-17
You can add both of those through synaptic. Administration > Synaptic package manager and then search for mysql and build-essential.

---

### Post by pronto32 on 2009-06-17
THanx Guys will look into it .

---

