---
title: "File permissions"
date: 2006-01-10
forum: Desktop Environments
---

### Post by AASZA on 2006-01-10
I just installed breezy badger and I have a few programs that I want to start at startup. I added them to the startup programs in sessions but when i log on they don't execute because i don't have root privileges.

How can you set it up so you have root privileges across the board ?

How can you setup root privileges for a single file/program?

---

### Post by frodon on 2006-01-10
Edit your /etc/sudoers file and add a line like that to give root priviliges to a program you want to launch on startup with root rights : ```
username ALL= NOPASSWD: /usr/bin/your_program
```Replace *username* with whatever your login is and */usr/bin/your_program* by the program you want to launch.

You should keep in mind that each person who will take the control of your user account will also take the control of the program you put here.

---

### Post by AASZA on 2006-01-10
:KS Thanxx

---

