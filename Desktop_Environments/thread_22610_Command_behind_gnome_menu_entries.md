---
title: "Command behind gnome menu entries"
date: 2005-03-28
forum: Desktop Environments
---

### Post by hal8000 on 2005-03-28
Using Ubanto Hoary 5.05 with Gnome 2.10.  How do you find the command line entry behind each gnome menu?  OK, I know that behind the Apllications/Internet/Firefox Web browser entry the command for the terminal would be firefox. But is there a way to view the command entries?
More specifically I would like to know how to launch the graphical synaptic package manager from the command line.   Thanks in advance.

---

### Post by PMO6022 on 2005-03-28
In a console you can type whereis <program> and it will tell you where the program is located.  For example: > pmorris@ubuntu:~/bin $ whereis synaptic
synaptic: /usr/sbin/synaptic /usr/share/synaptic /usr/share/man/man8/synaptic.8.gz Typically, you will just type the name of the program, "synaptic".

---

