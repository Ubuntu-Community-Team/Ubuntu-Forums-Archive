---
title: "How to create executable shortcuts on desktop"
date: 2006-04-09
forum: Desktop Environments
---

### Post by jlhughes on 2006-04-09
I have two commands that I normally execute in a terminal window:

sudo /opt/lampp/lampp start 

and 

sudo /opt/lampp/lampp stop

I'm new to KDE and new to Ubuntu. I want to create an icon on the KDE desktop that I can click to execute the commands. How do I do this?

---

### Post by nanotube on 2006-04-09
[QUOTE=jlhughes]I have two commands that I normally execute in a terminal window:

sudo /opt/lampp/lampp start 

and 

sudo /opt/lampp/lampp stop

I'm new to KDE and new to Ubuntu. I want to create an icon on the KDE desktop that I can click to execute the commands. How do I do this?[/QUOTE]

just create two simple shell scripts, with the following commands in them, make them executable, and you will have your shortcuts.

the contents of the two files should be:
```
#!/bin/bash
sudo /opt/lampp/lampp stop
```
and the other one the same, but with "start". 
make these two text files and put them on the desktop, then make them executable by 
```
chmod u+x filename
```
where filename is the name for your file. 
now you can just doubleclick one of those, and it will run.

---

### Post by shakin on 2006-04-10
Right click on the desktop and select Create New -> Link to Application.

From there you can just type in the command you want to run.

---

