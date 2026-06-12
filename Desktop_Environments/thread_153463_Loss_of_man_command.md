---
title: "Loss of man command?"
date: 2006-04-01
forum: Desktop Environments
---

### Post by Oddvar on 2006-04-01
I have installed and updated regularly Ubuntu 5.10
Wirhout me doing any action , like remove or delete, I get the message
when I try to use the man command:

bash: man: command not found

I have searced for man files, and find 1048 files.....

---

### Post by hw-tph on 2006-04-01
Welcome to the forums, Oddvar. :)

This sounds very odd. Try reinstalling man-db: **sudo apt-get install man-db**.


Håkan

---

### Post by Oddvar on 2006-04-02
[QUOTE=hw-tph]Welcome to the forums, Oddvar. :)

This sounds very odd. Try reinstalling man-db: **sudo apt-get install man-db**.


Håkan[/QUOTE]
 Håkan: These are the messages after sudo:

oddvar@ubuntu:~$ sudo apt-get install man-db
Password:
Reading package lists... Done
Building dependency tree... Done
man-db is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oddvar@ubuntu:~$ man ls
bash: man: command not found
oddvar@ubuntu:~$

---

